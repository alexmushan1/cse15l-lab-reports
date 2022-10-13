**CSE 15L lab 3 report**

Alex Zhang

**part 1** Search Engine

# code block
import java.io.IOException;
import java.net.URI;
import java.util.ArrayList;

class Handler implements URLHandler {
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.
    int num = 0;
    ArrayList<String> alist = new ArrayList<String>();
    
    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            return String.format("Number: %d", num);
        } else if (url.getPath().equals("/increment")) {
            num += 1;
            return String.format("Number incremented!");
        } else {
            System.out.println("Path: " + url.getPath());
            if (url.getPath().contains("/add")) {
                String[] parameters = url.getQuery().split("=");
                if (parameters[0].equals("count")) {
                    num += Integer.parseInt(parameters[1]);
                    return String.format("Number increased by %s! It's now %d", parameters[1], num);
                }
                if (parameters[0].equals("s")) {
                    alist.add(parameters[1]);
                    return "added "+parameters[1];
                }
            }
            else if (url.getPath().contains("/search")){
                ArrayList<String> blist = new ArrayList<String>();
                String[] parameters = url.getQuery().split("=");
                if (parameters[0].equals("s")) {
                    for (String s : alist){
                        if (s.contains(parameters[1])){
                            blist.add(s);
                        }
                    }
                    return "result="+blist;
                }
            }
            return "404 Not Found!";
        }
    }
}

class SearchEngine {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}

![Image](cse%2015l%20lab%203%20pt1%20p5.png)
we first log in using ssh and set up our server.
We have to cd into the write place and compile the code.
then we can run the server.
![Image](CSE%2015l%20lab%203%20pt1%20p1.png)
handleRequest is called, it reads the URL. reads add and add the word after "=" to a list.
![Image](CSE%2015l%20lab%203%20pt1%20p2.png)
![Image](CSE%2015l%20lab%203%20pt1%20p3.png)
continues to add more words.
![Image](CSE%2015l%20lab%203%20pt1%20p4.png)
Finally if we do search key, we should only see the two words that contains key. Search runs a loop to check the existing words in the arraylist and return a new list with the chosen words.

**Part 2** two bugs

Bug 1:

my failure-inducing input for reversed is [1,2,3,4] but result I get is arrays first differed at element [0]; expected:<4> but was:<0> (Symptom)
![Image](cse%2015l%20lab%203%20pt2%20p1.png)
the problem is we created a new array and instead of modifying the new array, we are assigning the value in the new array to the old array and returning the old array, resulting in all 0 in the array.(bug)

![Image](cse%2015l%20lab%203%20pt2%20p2.png)
to fix it, we have to modify the new array instead of arr. We swap newArray and arr, and then at the end we have to return the new array instead of the old one.(fix)

because the symptom produces 0 in the array, so that empty arrays will pass the test. only when you have contente other than 0 in the test, the bug will cause the code to produce the wrong output.


Bug 2:

The failure-inducing output for the filter is [a,b,longword], my filter uses a string checker that checks for short words under length of 5. The expected output should be [a,b] but the actual output gave arrays first differed at element [0]; expected:<[a]> but was:<[b]>. The element in the first index is different. 

![Image](cse%2015l%20lab%203%20pt2%20p3.png)

Below is my test ran against the code.
![Image](cse%2015l%20lab%203%20pt2%20p4.png)

The reason is in the filter method, if the filter is true, it adds the element to index 0 to result. So it kept adding to the same index 0 and replacing it with each element that fits the criteria. So there is only one element in the ArrayList. 

![Image](cse%2015l%20lab%203%20pt2%20p5.png)
to fix it, you just need to remove the “0,” in add, the program should run fine.

If you have only one element that fits the critieria in the arraylist, then the symptom won't appear. When you start to have multiple that fits the criteria in the arraylist, the bug will start causing the symptom because the returned list is only updating at index 0 instead of adding on to it.