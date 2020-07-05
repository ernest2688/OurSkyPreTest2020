Function isSubset 
Inputs A: Array of Char , B: Array of Char 
Returns Bool 
Variables i,j: Integer , flag: Bool (with default value false)

Begin

for i:= 0 to size(B)-1 do
    flag:=false;
    for j:=0 to size(A)-1 do 
        if(A[j]=B[i]) then
            flag:=true;
    fi
    od
    if(!flag) then
        break;
    fi
od 
return flag;

End

Explaination:
---------------------------------------------------------------------
The outer loop is the scanning of the 2nd array.I assume the second
array is shorter. Then the inner loop is for checking whether each
element of the second array is included in the first array. So the
overall complexity would be O(n^2).

Possible preprocessing work could be sorting both array to be accending
order(i.e. quicksort).
