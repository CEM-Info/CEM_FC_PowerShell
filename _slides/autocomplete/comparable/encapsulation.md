---
title: Encapsulation
nav_order: 4
---

One important design decision about the `CalendarDate` class is the use of **private fields**. By declaring fields `private`, they allow access and modification only by code defined inside the implementing class. This helps to ensure external correctness by preventing clients from unexpectedly modifying important values.

```java
public class CalendarDate {
    private int year;
    private int month;
    private int day;
}
```
{: overlay="Implementer" }

```java
public class Calendar {
    public static void main(String[] args) {
        CalendarDate welcome = new CalendarDate(2020, 9, 30);
        // private access prevents the following line of code from compiling
        welcome.day = 31;
    }
}
```
{: overlay="Client" }

In programming, this idea of preventing unexpected changes to the fields of an object is **encapsulation**. However, the `private` keyword prevents both access and modification, so it prevents clients from accessing (reading) the value of the current `day`.

### Getters and setters

To selectively allow access to fields, implementers can add **getter** methods that return copies of fields.

```java
public class CalendarDate {
    private int year;
    private int month;
    private int day;

    public int year() {
        return year;
    }

    public int month() {
        return month;
    }

    public int day() {
        return day;
    }
}
```
{: overlay="Implementer" }

This allows clients to access the current day without allowing unintended modification.

```java
CalendarDate welcome = new CalendarDate(2020, 9, 30);
int wednesday = welcome.day();
wednesday = 31;
```
{: overlay="Client" }

<details markdown="1">
<summary>Why doesn't reassigning wednesday change the welcome object?</summary>

`int wednesday` is a local variable assigned a copy of the number representing the `welcome` day. Changes to the local variable won't affect the encapsulated `welcome` object.
</details>

To selectively allow modification of fields, implementers can add **setter** methods.

```java
public class CalendarDate {
    private int year;
    private int month;
    private int day;

    public void setYear(int year) {
        this.year = year;
    }
}
```
{: overlay="Implementer" }

Since getters and setters are methods, they can include extra code to validate and check any of the given parameters.

```java
public class CalendarDate {
    private int year;
    private int month;
    private int day;

    public void setDate(int year, int month, int day) {
        // Check that the date is valid!
        validateDate(year, month, day);
        this.year = year;
        this.month = month;
        this.day = day;
    }
}
```
{: overlay="Implementer" }
