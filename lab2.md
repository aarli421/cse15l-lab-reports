## Part 1
This part asks for a web server written from java called StringServer, which displays a message that can be added to through the following request:
```
/add-message?s=<string>
```
These requests are handled by the Handler class as displayed in the code block below. It checks if the URL request fits the format above, where it will concatenate the queried string. If not, the website would just display the current stored message. The web server is instantiated within the main method, where command line arguments are used to get the port number in the main method. The server is also told to call upon the Handler class within the file to handle any URL requests.
```
import java.io.IOException;
import java.net.URI;

class Handler implements URLHandler {
    String message = "";

    public String handleRequest(URI url) {
        if (url.getPath().contains("/add-message")) {
            String[] parameters = url.getQuery().split("=");
            message += parameters[1] + "\n";
        }

        return message;
    }
}

class StringServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);
        Server.start(port, new Handler());
    }
}
```
The following screenshot shows the result of doing the add message request for the first time. Essentially, when the website gets a request, it will call the **handleRequest** method. This method takes in a url as its argument, which will then be checked to see if it matches any query. If it does, it will run the corresponding code. In this case, since the **/add-message** query was called, it gets the parameter of the url and adds it to the message. Since this is our first time running **/add-message**, the message value is currently empty. This request sets the message value to "Hello" because it is appended to the string.
![Screenshot 2023-01-30 at 2 42 57 PM](https://user-images.githubusercontent.com/35825663/215612978-8fa901ac-4df4-48c8-8dd2-3b0ed7be2ef1.png)

The following screenshot shows the result after querying the add message request again. Once again, the **handleRequest** method within the Handler class gets called and the url is passed as the method's value. This url is then checked if it matches any query. Since the query matches with **/add-message**, the parameter of the url is extracted and added to the message. This time, the message value already has "Hello\n" stored in the message. Thus, when adding another string, it is added after the "Hello" to result in "Hello\nHow are you".
![Screenshot 2023-01-30 at 2 43 20 PM](https://user-images.githubusercontent.com/35825663/215613028-1da8bf5a-8e30-45a5-a59c-c3d7d95ddaef.png)

## Part 2
This part asks for a bug from Lab 3 and the steps we took to fixing this bug. The bug I encountered was within the ListExamples filter method. The method was to filter a list by a certain StringChecker, and then return all these elements in the same order they appeared in the list. However, a buggy input is included below that did not follow what the program intended. Although the output of this test case should have been in the same order that the elements appeared in the list, the code actually outputted it in reverse order.
```
@Test
public void testFilter() {
    List<String> input = new ArrayList<>();
    input.add("one");
    input.add("two");
    input.add("three");

    StringChecker sc = new StringChecker() {
        @Override
        public boolean checkString(String s) {
            return s.contains("e");
        }
    };

    List<String> output = ListExamples.filter(input, sc);

    assertEquals("[one, three]", output.toString());
}
```
This bug does not always happen, however. The following code is an input that does not produce this bug. This is because the output is only one element long, so the program does not have enough outputs for the bug to be reproduced.
```
@Test
public void testFilterCorrect() {
    List<String> input = new ArrayList<>();
    input.add("one");
    input.add("two");
    input.add("three");

    StringChecker sc = new StringChecker() {
        @Override
        public boolean checkString(String s) {
            return s.contains("w");
        }
    };

    List<String> output = ListExamples.filter(input, sc);

    assertEquals("[two]", output.toString());
}
```
The following screenshot shows the symptom after running both input tests above. Only one of the test cases resulted in the error because one of them is able to pass. The test case that did fail describes the error in detail. Although we expected "[one, three]", the output was in reverse order as "[three,one]".
<img width="955" alt="Screenshot 2023-01-30 at 3 15 09 PM" src="https://user-images.githubusercontent.com/35825663/215618063-f7d42d81-1978-46a8-a3ae-e3e066ba8939.png">
After understanding the errors, we can now look at the code that created these bugs. The following is the code that caused the faulty testcases.
```
static List<String> filter(List<String> list, StringChecker sc) {
    List<String> result = new ArrayList<>();
    for (String s: list) {
        if (sc.checkString(s)) {
            result.add(0, s);
        }
    }
    return result;
}
```
The code can be fixed by changing the line **result.add(0, s);** to **result.add(s);** as shown below.
```
static List<String> filter(List<String> list, StringChecker sc) {
    List<String> result = new ArrayList<>();
    for (String s: list) {
        if (sc.checkString(s)) {
            result.add(s);
        }
    }
    return result;
}
```
This addresses the bug because instead of adding each item at the front of the list, we just append it to the back of the list. To keep the correct order of elements, every element we see should be added after the elements we have seen before. Thus, you would append new elements to the back of the list instead of adding it to the front.

## Part 3
Within lab week 2, I learned how to create a web server out of Java for the first time. I found it really cool that websites can be so easily created and it is interesting to think that a lot of websites out there are probably created using this method, albeit with different languages and libraries. Furthermore, it is interesting how different users can manipulate the same server stored variables on the website.
