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

```
class Handler implements URLHandler {
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.
    ArrayList<String> list = new ArrayList<String>();

    public String handleRequest(URI url) {
        // checks if path is "empty"
        if (url.getPath().equals("/")) {
            return String.format("Here is whats in the List!\n" + String.join(", ", list));
        } else if (url.getPath().equals("/addFiller")) {
            list.add("filler");
            return String.format("it added the word \"filler\"!");
        } else {
            System.out.println("Path: " + url.getPath());

            // Code for Adding
            if (url.getPath().contains("/add")) {
                String[] parameters = url.getQuery().split("=");
                // if we in fact are adding.... check for the "a"
                if (parameters[0].equals("a")) {
                    list.add(parameters[1]);
                    return String.format("Added " + parameters[1] + " to the List!");
                }
            }

            else if (url.getPath().contains("/query")) {
                // Code for Searching
                String[] parameters = url.getQuery().split("=");
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
            }

            return "bruh wtf error code 404 up in here\n you fucked up lol";
        }
    }
}
```
Here it is in action:

After launching, it looks like this after i go to the link:

    http://localhost:4000/

>![image](/r2images/SE1.png)
> As you can see, there are no entries in the list

I am going to add the word "silly" to the list by going to this link: 

    http://localhost:4000/add?a=silly

I can change what I want to add by inputting any string after the ``a=``


Now if we go back to the localhost, we can see that it was added!

>![image](/r2images/SE2.png)


I am going to add another word called "sillybilly" which contains the word "silly"
>![image](/r2images/SE3.png)


Now by going to the following link, I am going to search for "silly"

    http://localhost:4000/query?s=silly

>![image](/r2images/SE4.png)
>as you can see, it returned both silly and sillybilly as "search results"