# Weeks 2 & 3 Lab Report

***Contents:***

Week 2: Web Servers
- Simple "Search Engine"

Week 3: Testing and Debugging
- Setting up JUnit
- Debugging Array
- Debugging Linked List

---------------

## Week 2: Web Server Search Engine
    
Because you guys asked,  here is the single large class that my search engine is implemented through!


*Main Body*

```
public String handleRequest(URI url) {
        // checks if path is "empty"
        if (url.getPath().equals("/")) {
            return String.format("Here is whats in the List!:\n" + String.join(", ", list));
        } else if (url.getPath().equals("/addFiller")) {
            list.add("filler");
            return String.format("it added the word \"filler\"!");
        } else {
            System.out.println("Path: " + url.getPath());
            String[] parameters = url.getQuery().split("=");
            // Code for Adding
            if (url.getPath().contains("/add")) {
                return add(parameters);
            }

            else if (url.getPath().contains("/query")) {
                // Code for Searching
                    return search(parameters);
                }
            }

            return "bruh wtf error code 404 up in here\n you fucked up lol";
        }
    }
```

**add function**
```
public String add(String[] parameters){
    // if we in fact are adding.... check for the "a"
    if (parameters[0].equals("a")) {
        list.add(parameters[1]);
        return String.format("Added " + parameters[1] + " to the List!");
    }
}
```
**search function**
```
public String search(String[] parameters){
    // if we in fact are searching.... check for the "s"
    if (parameters[0].equals("s")) {
        ArrayList<String> tempList = new ArrayList<String>();
        Iterator iter = list.iterator();
        while (iter.hasNext()) {
            String temp = (String) iter.next();
            if (temp.contains(parameters[1])) {
                tempList.add(temp);
            }
        }

        return String.format("Result(s): " + String.join(", ", tempList));
}

```

Here it is in action:

For all pages/screenshots below, the handleRequest method is called which will itself call more methods.

After launching, it looks like this after i go to the link:

    http://localhost:4000/

>![image](/r2images/SE1.png)
> As you can see, there are no entries in the list. 
>
> In my code, if the path is "/", then it goes to the default page. No methods are called, and only the default message is returned

I am going to add the word "silly" to the list by going to this link: 

    http://localhost:4000/add?a=silly



Now if we go back to the localhost, we can see that it was added!

>![image](/r2images/SE2.png)
>handleRequest stores the whole path into an array, and searches the path for "/add". Because it was in there, it calls and returns the add() method.
>
>In the add() method, the path array was passed into it, and it adds the string after the "=" to the list of words stored.

I am going to add another word called "sillybilly" which contains the word "silly". You can see that the search engine has those two entries stored here:
>![image](/r2images/SE3.png)


Now by going to the following link, I am going to search for "silly"

    http://localhost:4000/query?s=silly

>![image](/r2images/SE4.png)
>as you can see, it returned both silly and sillybilly as "search results"
>
>When the handeler saw that the path contained "/query", it called the search method. Similar to the add() method, it was passed the array containing the query. Then, it would iterate through the list of stored "search results" and return the ones who contained "silly" which would be both words. The list itself is not modified, and a new one is returned.







----------

## Week 3: Testing and Bug Fixing



In this lab, we saw many methods for implementations of various classes that were buggy, and tested to identify and fix them.

The instances I will show you today are the ListExample and LinkedListExample methods.



### *ListExample*

These are the tests I wrote to test ListExample. There are two tests for filler() and one test for merge()

```
 @Test
  public void testFilter(){
    List<String> input = new ArrayList<String>(List.of("aa","b","aa","ccc","aa"));
    StringChecker sc = new lenTwoStringChecker();
    List<String> output = ListExamples.filter(input, sc);
    assertArrayEquals(new ArrayList<String>(List.of("aa", "aa", "aa")).toArray(), output.toArray());

  }

  @Test
  public void testFilter2(){
    List<String> input = new ArrayList<String>(List.of("aa","b","cc","ddd","ee"));
    StringChecker sc = new lenTwoStringChecker();
    List<String> output = ListExamples.filter(input, sc);
    assertArrayEquals(new ArrayList<String>(List.of("aa", "cc", "ee")).toArray(), output.toArray());

  }
```


```
  @Test
  public void testMerge(){
    List<String> input = new ArrayList<String>(List.of("a","b","c","d","e"));
    List<String> input2 = new ArrayList<String>(List.of("aa","bb","cc","dd","ee"));
    List<String> output = ListExamples.merge(input,input2);
    assertArrayEquals(new ArrayList<String>(List.of("a","aa","b","bb","c", "cc","d","dd","e", "ee")).toArray(), output.toArray());
    

  }
```

> This is an image of ListExamples failing Filler() tests, specifically
>![image](/r2images/LEbug.png)

The input that produced an error was passing an array with strings that were all different.



 eg.:
- `["aa","b","cc","ddd","ee"] ` would fail
- `["aa","b","aa","ccc","aa"]` would pass
