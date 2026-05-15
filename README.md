# Step 1 — Explain JSON Conceptually

## What is JSON?

JSON stands for:

> JavaScript Object Notation

It is simply a way to store data using text.

## Example

```json
{
  "recipient": "+27718693002",
  "message": "Hi Mike, can you join us for dinner tonight?"
}
```

> “JSON is like a digital form of storing objects.”

---

# Step 2 — Create a Java Maven Project in NetBeans

## In NetBeans

### 1. Create a New Project

Go to:

```text
File → New Project
```

Choose:

```text
Java with Maven
```

Then select:

```text
Java Application
```

Click:

```text
Next
```

---

## 2. Project Name

Example:

```text
QuickChatJSON
```

Click:

```text
Finish
```

---

# Step 3 — Add Gson Library

Explain:

> “Maven automatically downloads libraries for us.”

Open:

```text
pom.xml
```

You will see something like this:

```xml
<project>
```

Inside the `<dependencies>` section add:

```xml
<dependencies>

    <dependency>
        <groupId>com.google.code.gson</groupId>
        <artifactId>gson</artifactId>
        <version>2.10.1</version>
    </dependency>

</dependencies>
```

Right-click the project and select:

```text
Clean and Build
```

Maven downloads Gson automatically.

---

# Step 4 — Create a Simple Message Class

Create a class called:

```text
Message.java
```

## Example

```java
public class Message {

    private String recipient;
    private String message;

    public Message(String recipient, String message) {
        this.recipient = recipient;
        this.message = message;
    }

    public String getRecipient() {
        return recipient;
    }

    public String getMessage() {
        return message;
    }
}
```

---

# Step 5 — Create Main Class

Open:

```text
Main.java
```

---

# Step 6 — Import Gson

```java
import com.google.gson.Gson;
```

---

# Step 7 — Create Object

```java
Message msg = new Message(
        "+27718693002",
        "Hi Mike, can you join us for dinner tonight?"
);
```

---

# Step 8 — Convert Object to JSON

```java
Gson gson = new Gson();

String json = gson.toJson(msg);

System.out.println(json);
```

## Output

```json
{"recipient":"+27718693002","message":"Hi Mike, can you join us for dinner tonight?"}
```

---

# Step 9 — Store JSON into File

Now introduce file handling.

## Import

```java
import java.io.FileWriter;
import java.io.IOException;
```

---

# Full Example

```java
import com.google.gson.Gson;
import java.io.FileWriter;
import java.io.IOException;

public class Main {

    public static void main(String[] args) {

        // Create Java object
        Message msg = new Message(
                "+27718693002",
                "Hi Mike, can you join us for dinner tonight?"
        );

        // Convert object to JSON
        Gson gson = new Gson();

        String json = gson.toJson(msg);

        // Display JSON
        System.out.println(json);

        // Store JSON into file
        try {

            FileWriter writer = new FileWriter("message.json");

            writer.write(json);

            writer.close();

            System.out.println("JSON saved successfully.");

        } catch (IOException e) {

            System.out.println("An error occurred.");
        }
    }
}
```

---

# File Handling

## What is Happening?

### FileWriter

Creates or opens a file.

### writer.write(json)

Writes the JSON data into the file.

### writer.close()

Closes the file properly.

### try-catch

Used for error handling.

---

# Expected File Output

A file called:

```text
message.json
```

Will contain:

```json
{"recipient":"+27718693002","message":"Hi Mike, can you join us for dinner tonight?"}
```

