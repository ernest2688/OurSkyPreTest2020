**********************************************************************
Assumption: - using linear probing as collusion solution.
            <br>
	    - the hash table is an array with size:= m
	    <br>
	    - key value is an integer (for simplicity)
	    <br>	    
	    - the hash function is h(k)=k mod m, where k is the key and m is the size of the hash table, usually prime. 
	    <br>
	    - the overall structure is that there is an array storing a sturcture which has the key attribute,value attribute and weight attribute
	    <br>
            - if there is no key and value stored, default the attribute of the struct will be key=0, value=0, weight=0
	    <br>
	    - after inserting n records, the average list length should be abput n/m.
*******************************************************************		


Function get(key)
Inputs key: key value
Returns:int
Variables  i,m,k:integer (m is the size of hash table) T:array (hash table)

Begin

for i:=0 to i:=m-1 do
    k:=(h(k) + i ) mod m;
    if(T[k].key = key) 
        return T[k].value;
    fi

    if(T[k].key=0 && T[k].value=0)
    break;
    fi

od
return -1;
End

Explanation: If direct hashing is hits the key, then we can directly return the value. If not, walk through the array to find the required key, 
then return the value. There are two stopping case. First is that the the key is not found after walkthrough the whole array. 
The second is when you meet an empty struct. This two case can result in the cound not found result.
Since it is direct mapping, the best/average case of complaxity could be O(1). The worst case would be O(n).





Function put(key, value, weight) 
Inputs key: key value value: the value to be stored weight: the number using for invalidating keys
Returns void
Variables i,k,score,min:integer (min default value:=0)

Begin
for i:=0 to i:=m-1 do
    k:=(h(k) + i ) mod m;
    if(T[k].key = 0 && T[k].value=0) 
        T[k].key=key;
	T[k].value=value;
	T[k].weight=weight;
	return;
    fi

for i:=0 to i:=m-1 do
    if(current_time != last_access_time) 
	score:= weight / ln(current_time - last_access_time);
    else score:= weight / -100;    
    fi
    if(score<=min)
	min:=score;
        k:=i;
    fi
od

T[k].key=key;
T[k].value=value;
T[k].weight=weight;
return;
End
    
Explanation: It is quite similar to the get function. The difference is that it will fit if empty struct is found. 
However, if all the structs are occupied, then it will search the struct with the least score given by the calculation,
and the key, value,and the weight is stored to the calculated destination. For hashing, the big O is with worst case of O(n), 
and finding minimum requires O(n) complexity. So the worst case is still O(n). While the best case/ average case could remain as O(1).      




