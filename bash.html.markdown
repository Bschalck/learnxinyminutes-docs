---
name: bash
category: language
language: bash
filename: learnbash.bash
contributors:
    - ["Baptiste SCHALCK", "http://www.devloprog.org/"]
---

BASH as Bourne Advance SHell 
Good stuff on Unix/ Linux and other distrib


```c
# Single-line comments start with #

#
#Multi-line comments does NOT exist
#

Begin a script with the SheBang
#!/bin/bash

# Import headers with #include
source myfile.sh



function_1() {
  # paramaters are known as $1, $2 ,$3
  # list of parameters is $*
  # number of parameters is $#

}

#define a simple varaiable
var="World";
#There is no type of variable
nbvar=5
echo "Hello ${var}!We are ${nbvar} ! " # will show-> Hello World!We are 5 !

#But if you really want to set your variable, you can :)
########################################
// Types
########################################
#!/bin/bash

func1 ()
{
  echo This is a function.
}

declare -f        # Lists the function above.

echo

declare -i var1   # var1 is an integer.
var1=2367
echo "var1 declared as $var1"
var1=var1+1       # Integer declaration eliminates the need for 'let'.
echo "var1 incremented by 1 is ${var1}."
# Attempt to change variable declared as integer.
echo "Attempting to change var1 to floating point value, 2367.1."
var1=2367.1       # Results in error message, with no change to variable.
echo "var1 is still $var1"

#declare -r var1 works the same as readonly var1

declare -r var2=13.36         # 'declare' permits setting a variable property
                              #+ and simultaneously assigning it a value.
echo "var2 declared as $var2" # Attempt to change readonly variable.
var2=13.37                    # Generates error message, and exit from script.

# Arrays must be initialized with a concrete size.
declare -A a         # declare an associative array 'a' faking a bi-dimensional indexed array
i=1; j=2             # initialize some indices
a[$i,$j]=5           # associate value "5" to key "$i,$j" (i.e. "1,2")
echo ${a[$i,$j]}     # print the stored value at key "$i,$j"


tab[0]=val           #affect the first key of the array tab
echo ${tab[0]}       # will show "val"
${tab[*]}            # show all entries in the array
${#tab[11]}          #show size of the 11 elements of the array
${#tab[*]}           #show count of entries in the array

########################################
## Control Structures
########################################

################
# test with if #
################
 #!/bin/bash

a=4
b=5

#  Here "a" and "b" can be treated either as integers or strings.
#  There is some blurring between the arithmetic and string comparisons,
#+ since Bash variables are not strongly typed.

#  Bash permits integer operations and comparisons on variables
#+ whose value consists of all-integer characters.
#  Caution advised, however.

echo

if [ "$a" -ne "$b" ]
then
  echo "$a is not equal to $b"
  echo "(arithmetic comparison)"
fi

echo

if [ "$a" != "$b" ]
then
  echo "$a is not equal to $b."
  echo "(string comparison)"
  #     "4"  != "5"
  # ASCII 52 != ASCII 53
fi

# In this particular instance, both "-ne" and "!=" work.

## TEST with more than 1 condition (( && == AND , ||== OR ))
a=3

if [ "$a" -gt 0 ]
then
  if [ "$a" -lt 5 ]
  then
    echo "The value of \"a\" lies somewhere between 0 and 5."
  fi
fi

# Same result as:

if [ "$a" -gt 0 ] && [ "$a" -lt 5 ]
then
  echo "The value of \"a\" lies somewhere between 0 and 5."
fi

############
# For loop #
############
for planet in Mercury Venus Earth Mars Jupiter Saturn Uranus Neptune 
do
  echo $planet  # Each planet on a separate line.
done

 #!/bin/bash
for i in `seq 1 10`;# seq command will return 1 2 3 4 ... 10 
do
       echo $i
done    
        
################
# While loop   #
################
#!/bin/bash 
COUNTER=0
while [  $COUNTER -lt 10 ]
do
	echo "The counter is ${COUNTER}"
	((COUNTER++))
done
################################
# Double-Parentheses Construct #
################################

(( a = 23 ))  #  Setting a value, 
              #+ with spaces on both sides of the "=".
echo "a (initial value) = $a"   # 23

(( a++ ))     #  Post-increment 'a', 
echo "a (after a++) = $a"       # 24

(( a-- ))     #  Post-decrement 'a', 
echo "a (after a--) = $a"       # 23


To be continued ....
