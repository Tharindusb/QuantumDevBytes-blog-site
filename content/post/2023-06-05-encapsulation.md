---
title: Encapsulation
subtitle: Safeguarding Data and Enhancing Code Flexibility
date: 2023-06-05
tags: ["ObjectOrientedProgramming","Java","BackToBasics"]
---

Encapsulation in OOP refers to the bundling of data and methods within a class, hiding the internal implementation details and providing controlled access through well-defined interfaces.

<!--more-->

In the following example, I illustrate a scenario where lack of encapsulation can lead to potential issues:

```java
    public class Car{
        String licenPlateNumber;
        float millage;
    }
```

In this code snippet, the licensePlateNumber and mileage variables are publicly accessible. Anyone can easily access and modify these variables directly.


```java
    public static void main(String[] args){
        Car car = new Car();
        car.licenPlateNumber = "ABC123";
    }

```

To address this issue, encapsulation can be employed:

```java
    public class Car{
        private String licenPlateNumber;
        private float millage;

        public void setLicenPlateNumber(String number){
            licenPlateNumber = number;
        }

        public String getLicenPlateNumber(){
            return licenPlateNumber
        }
    }
```

By using the private access modifier for the variables and providing setter and getter methods, we control the access to the data.

Now, consider the updated code snippet that demonstrates encapsulation in action: 

```java
    public static void main(String[] args){
        Car car = new Car();
        car.setLicenPlateNumber("ABC123");
        System.out.println(car.getLicenPlateNumber());
    }
```

In this revised code, the `setLicensePlateNumber()` method is used to set the license plate number, and the `getLicensePlateNumber()` method is used to retrieve the value. This way, access to the data is regulated, and we can ensure proper encapsulation and maintain data integrity.

By embracing encapsulation, we enhance the readability, maintainability, and reliability of our code, and we establish a clear and controlled way to interact with the data within our objects.