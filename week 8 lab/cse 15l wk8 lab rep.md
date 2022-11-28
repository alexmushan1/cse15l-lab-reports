**lab report 5**

Alex Zhang

```
# Create your grading script here

#set -e
rm -rf err.txt
rm -rf student-submission
git clone $1 student-submission

CP=".:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar"

cd student-submission

if ! [[ -e ListExamples.java ]]
then 
    echo "file not found"
    exit 1
else
    echo "file found"
    cp ListExamples.java ./../
    cd ..
    javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java 2> err.txt
fi

echo
[ -s err.txt ]

if  [[ $? -eq 0 ]]
then
    echo "does not compile"
    exit 1
else
    echo "compiled successfully"
fi
    
#Score=0

java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore TestListExamples > output.txt

#if [[ $? -eq 1 ]]
#then
 # Score=$(($Score+1))
#fi
#echo "Your score is" $Score
#echo < output.txt 
echo

FTests=$(grep -o "ListExamples.filter(" TestListExamples.java | wc -l)

MTests=$(grep -o "ListExamples.merge(" TestListExamples.java | wc -l)

Filter=$(grep -o "testFilter" output.txt | wc -l)

Merge=$(grep -o "testMerge" output.txt | wc -l)

FPassed=$(echo "$FTests-$Filter/2" | bc)

MPassed=$(echo "$MTests-$Merge/2" | bc)

echo "you passed $FPassed out of $FTests test for filter() method!"

echo

echo "you passed $MPassed out of $MTests for merge() method!"
```


![1](cse%2015l%20lab%20rep%205%201.png)
![2](cse%2015l%20lab%20rep%205%202.png)
![3](cse%2015l%20lab%20rep%205%203.png)


Trace:

for the second output using the compile error github link:

the first few lines pass without any problem, until the if statment. 

the first if statment is false because we are able to find the file using -e. I was using a ! for not, so if we don't find it, it's true and return file not found and exit 1. else it is found and proceed.

then the following lines are able to run until we reach the javac command. since this code has a compile error, it was not able to complie, so the error is redirected to err.txt by using 2> after the javac command. this line returns a nonzero number indicating it is not a stdout.

the next line we echo if err.txt exists and has size greater than 0 by using the -s option. 

since err.txt was produced, this line will return 0.

the second if statment, we check if last output was 0 or not. if it was that means err.txt was produced, then we would say it did not compile and exit 1. so this if statment is true.

all the lines after else did not run, because we exited early after the if statment. line 30-62 will not run.