# Lab report 5
---
## Question on Grading Script
<img width="800" alt="Screen Shot 2023-06-05 at 8 40 34 PM" src="https://github.com/pameza/cse15l-lab-reports/assets/130017007/c8959e87-49e7-4670-98b4-e7123b171e09">

<img width="670" alt="Screen Shot 2023-06-05 at 8 37 08 PM" src="https://github.com/pameza/cse15l-lab-reports/assets/130017007/b1c172d4-5b3e-4c21-9476-1517d4ce1023">
[^1]: This student is having issues running their Grading Script from week 6.

---

<img width="829" alt="Screen Shot 2023-06-05 at 9 07 49 PM" src="https://github.com/pameza/cse15l-lab-reports/assets/130017007/49d29c84-679f-409e-8ea3-a8a0448ffc3b">

<img width="700" alt="Screen Shot 2023-06-05 at 9 00 21 PM" src="https://github.com/pameza/cse15l-lab-reports/assets/130017007/5d807245-bee2-4b0a-a29b-15e0c55f4c98">

---
<img width="250" alt="Screen Shot 2023-06-05 at 9 03 17 PM" src="https://github.com/pameza/cse15l-lab-reports/assets/130017007/29986b1c-5718-4594-8995-fd2c3be67cce">

<img width="634" alt="Screen Shot 2023-06-05 at 9 03 53 PM" src="https://github.com/pameza/cse15l-lab-reports/assets/130017007/fc7ed7de-1da9-4064-86f3-abbe105a1cd6">
---
### Information
<img width="183" alt="Screen Shot 2023-06-05 at 9 22 23 PM" src="https://github.com/pameza/cse15l-lab-reports/assets/130017007/abd57614-3f39-4f39-b7eb-17f44473b70c">
[^1]: The file & directory structure.

```
CPATH='.:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar'

rm -rf student-submission
rm -rf grading-area

mkdir grading-area

git clone $1 student-submission
echo 'Finished cloning'


if [[ -f .student-submission/ListExamples.java ]]
then
	echo "found"
else
	echo "file not found"
	exit
fi

cp -r student-submission grading area

# Then, add here code to compile and run, and do any post-processing of the
# tests

javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar grading-area/*.java
```
[^1]: grade.sh contents.


```
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStream;
import java.io.InputStreamReader;
import java.net.URI;
import java.net.URISyntaxException;
import java.util.Arrays;
import java.util.stream.Stream;

class ExecHelpers {

  /**
    Takes an input stream, reads the full stream, and returns the result as a
    string.

    In Java 9 and later, new String(out.readAllBytes()) would be a better
    option, but using Java 8 for compatibility with ieng6.
  */
  static String streamToString(InputStream out) throws IOException {
    String result = "";
    while(true) {
      int c = out.read();
      if(c == -1) { break; }
      result += (char)c;
    }
    return result;
  }

  /**
    Takes a command, represented as an array of strings as it would by typed at
    the command line, runs it, and returns its combined stdout and stderr as a
    string.
  */
  static String exec(String[] cmd) throws IOException {
    Process p = new ProcessBuilder()
                    .command(Arrays.asList(cmd))
                    .redirectErrorStream(true)
                    .start();
    InputStream outputOfBash = p.getInputStream();
    return String.format("%s\n", streamToString(outputOfBash));
  }

}

class Handler implements URLHandler {
    public String handleRequest(URI url) throws IOException {
       if (url.getPath().equals("/grade")) {
           String[] parameters = url.getQuery().split("=");
           if (parameters[0].equals("repo")) {
               String[] cmd = {"bash", "grade.sh", parameters[1]};
               String result = ExecHelpers.exec(cmd);
               return result;
           }
           else {
               return "Couldn't find query parameter repo";
           }
       }
       else {
           return "Don't know how to handle that path!";
       }
    }
}

class GradeServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}

class ExecExamples {
  public static void main(String[] args) throws IOException {
    String[] cmd1 = {"ls", "lib"};
    System.out.println(ExecHelpers.exec(cmd1));

    String[] cmd2 = {"pwd"};
    System.out.println(ExecHelpers.exec(cmd2));

    String[] cmd3 = {"touch", "a-new-file.txt"};
    System.out.println(ExecHelpers.exec(cmd3));
  }
}

```
[^1]: GradeServer.java contents.


```
// A simple web server using Java's built-in HttpServer

// Examples from https://dzone.com/articles/simple-http-server-in-java were useful references

import java.io.IOException;
import java.io.OutputStream;
import java.net.InetSocketAddress;
import java.net.URI;

import com.sun.net.httpserver.HttpExchange;
import com.sun.net.httpserver.HttpHandler;
import com.sun.net.httpserver.HttpServer;

interface URLHandler {
    String handleRequest(URI url) throws IOException;
}

class ServerHttpHandler implements HttpHandler {
    URLHandler handler;
    ServerHttpHandler(URLHandler handler) {
      this.handler = handler;
    }
    public void handle(final HttpExchange exchange) throws IOException {
        // form return body after being handled by program
        try {
            String ret = handler.handleRequest(exchange.getRequestURI());
            // form the return string and write it on the browser
            exchange.sendResponseHeaders(200, ret.getBytes().length);
            OutputStream os = exchange.getResponseBody();
            os.write(ret.getBytes());
            os.close();
        } catch(Exception e) {
            String response = e.toString();
            exchange.sendResponseHeaders(500, response.getBytes().length);
            OutputStream os = exchange.getResponseBody();
            os.write(response.getBytes());
            os.close();
        }
    }
}

public class Server {
    public static void start(int port, URLHandler handler) throws IOException {
        HttpServer server = HttpServer.create(new InetSocketAddress(port), 0);

        //create request entrypoint
        server.createContext("/", new ServerHttpHandler(handler));

        //start the server
        server.start();
        System.out.println("Server Started! Visit http://localhost:" + port + " to visit.");
    }
}
```
[^1]: Server.java contents.


```
import static org.junit.Assert.*;
import org.junit.*;
import java.util.Arrays;
import java.util.List;

class IsMoon implements StringChecker {
  public boolean checkString(String s) {
    return s.equalsIgnoreCase("moon");
  }
}

public class TestListExamples {
  @Test(timeout = 500)
  public void testMergeRightEnd() {
    List<String> left = Arrays.asList("a", "b", "c");
    List<String> right = Arrays.asList("a", "d");
    List<String> merged = ListExamples.merge(left, right);
    List<String> expected = Arrays.asList("a", "a", "b", "c", "d");
    assertEquals(expected, merged);
  }
}

```
[^1]: TestListExamples.java contents.


```
import java.util.ArrayList;
import java.util.List;

interface StringChecker { boolean checkString(String s); }

class ListExamples {

  // Returns a new list that has all the elements of the input list for which
  // the StringChecker returns true, and not the elements that return false, in
  // the same order they appeared in the input list;
  static List<String> filter(List<String> list, StringChecker sc) {
    List<String> result = new ArrayList<>();
    for(String s: list) {
      if(sc.checkString(s)) {
        result.add(s);
      }
    }
    return result;
  }


  // Takes two sorted list of strings (so "a" appears before "b" and so on),
  // and return a new list that has all the strings in both list in sorted order.
  static List<String> merge(List<String> list1, List<String> list2) {
    List<String> result = new ArrayList<>();
    int index1 = 0, index2 = 0;
    while(index1 < list1.size() && index2 < list2.size()) {
      if(list1.get(index1).compareTo(list2.get(index2)) < 0) {
        result.add(list1.get(index1));
        index1 += 1;
      }
      else {
        result.add(list2.get(index2));
        index2 += 1;
      }
    }
    while(index1 < list1.size()) {
      result.add(list1.get(index1));
      index1 += 1;
    }
    while(index2 < list2.size()) {
      result.add(list2.get(index2));
      index2 += 1;
    }
    return result;
  }


}
```
[^1]: [TestListExamples.java](https://github.com/pameza/list-methods-corrected.git) contents (student submission example).

<img width="533" alt="Screen Shot 2023-06-05 at 9 31 17 PM" src="https://github.com/pameza/cse15l-lab-reports/assets/130017007/430f6cd9-0ed1-46fd-bae7-cb3ca54d6315">
[^1]: Faulty command line. Here, the issue was that the student was attempting to run this command locally without providing an input for the command-line argument required to fulfill `$1` written in `grade.sh`. Once the student gave the command an input, `grade.sh` was able to run its tests. To be more specific, the `bash grade.sh` command was missing the student submission repository URL after it.

---
## Reflection
During this second half of the quarter I learned to deal with directory problems that I faced very frequently when I took CSE 11. I had trouble understanding the process behind `javac` and `java`, as well as `cd` commands. I previosly accepted their formats and uses but now I understand that `javac` compiles the java file to make it executable and creates files of the classes it contains. This explains the creation of multiple `.class` files that mysteriosly appeared in my downloads folder. I had a lot of fun experimenting with things I found in `man`, editing in `vim` and using tab to autocomplete my directories. I can definietely see myself using these tools frequently in the future.
