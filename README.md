# Lab-7_202001098
# **Name : Parth Agarwal**
# **ID : 202001098**
# **Section A**

## **Based on the input ranges, we can identify the following equivalence classes:** <br>

1. Valid dates: The input triple (day, month, year) that represent a valid date in the Gregorian calendar, such as (3, 4, 1995).
2. Invalid dates: The input triple (day, month, year) that represent an invalid date, such as (31, 2, 2022) or (29, 2, 1900).
3. Out of range dates: The input triple (day, month, year) that are outside the allowed ranges, such as (0, 5, 2010) or (15, 13, 2005).
Based on these equivalence classes, we can design the following test cases:

**Tester Action and Input Data Expected Outcome**<br>

**Valid dates:**<br>
1) Calculate previous date for (15, 10, 2022) 14, 10, 2022
2) Calculate previous date for (1, 1, 2015) 31, 12, 2014
3) Calculate previous date for (31, 3, 2000) 30, 3, 2000

**Invalid dates:**<br>
1) Calculate previous date for (29, 2, 2022) Invalid date
2) Calculate previous date for (31, 4, 2010) Invalid date
3) Calculate previous date for (30, 2, 2000) Invalid date

**Out of range dates:**<br>
1) Calculate previous date for (0, 5, 2010) Invalid date
2) Calculate previous date for (15, 13, 2005) Invalid date
3) Calculate previous date for (31, 12, 1899) Invalid date

## **Boundary Value Analysis:**<br>
Using boundary value analysis, we can identify the following boundary test cases:
1) The earliest possible date: (1, 1, 1900)
2) The latest possible date: (31, 12, 2015)
3) The earliest day of each month: (1, 1, 2000), (1, 2, 2000), (1, 3, 2000),..., (1, 12, 2000)
4) The latest day of each month: (31, 1, 2000), (28, 2, 2000), (31, 3, 2000),..., (31, 12, 2000)
5) Leap year day: (29, 2, 2000)
6) Invalid leap year day: (29, 2, 1900)
7) One day before earliest date: (31, 12, 1899)
8) One day after latest date: (1, 1, 2016)<br>

Based on these boundary test cases, we can design the following test cases:<br>
Tester Action and Input Data Expected Outcome<br>

**Boundary Test Cases:**<br>
1) Calculate previous date for (1, 1, 1900) Invalid date
2) Calculate previous date for (31, 12, 2015) 30, 12, 2015
3) Calculate previous date for (1, 1, 2000) 31, 12, 1999
4) Calculate previous date for (31, 1, 2000) 30, 1, 2000
5) Calculate previous date for (29, 2, 2000) 28, 2, 2000
6) Calculate previous date for (29, 2, 1900) Invalid date
7) Calculate previous
<br>

## Program 1:
The function linearSearch searches for a value v in an array of integers a. <br>
If v appears in the array a, then the function returns the first index i, such that a[i] == v; otherwise, -1 is returned.<br>
```
int linearSearch(int v, int a[]){
    int i = 0;
    while (i < a.length){
      if (a[i] == v)
        return(i);
      i++;
    }
    return (-1);
  }
```

**Equivalence Partitioning:**
 
| Tester Action and Input Data     | Expected Outcome      |
| ------------- | :---: |
| v is present in a        | Index of v         |
| v is not present in a         | -1         |

**Boundary Value Analysis:**

| Tester Action and Input Data     | Expected Outcome      |
| ------------- | :---: |
| Empty array a        | -1         |
| v is present at the first index of a         | 0         |
| v is present at the last index of a length of a        | -1         |
| v is not present in a         | -1         |

![P1](https://user-images.githubusercontent.com/62084382/231537672-397be7f2-be41-43f7-9ae8-75392b525d2b.png)

<br>

## Program 2:
The function countItem returns the number of times a value v appears in an array of integers a.<br>
```
int countItem(int v, int a[]){
  int count = 0;
  for (int i = 0; i < a.length; i++){
    if (a[i] == v)
    count++;
  }
  return (count);
}
```
**Equivalence Partitioning:**

| Tester Action and Input Data     | Expected Outcome      |
| ------------- | :---: |
| v is present in a        | Number of times v appears in a         |
| v is not present in a         | 0         |

**Boundary Value Analysis:**

| Tester Action and Input Data     | Expected Outcome      |
| ------------- | :---: |
| Empty array a        | 0         |
| v is present once in a         | 1         |
| v is present multiple times in a        | Number of times v appears in a         |
| v is present at the first index of a         | 1         |
| v is present at the last index of a        | 1        |
| v is not present in a         | 0        |



<br>

## Program 3:
The function binarySearch searches for a value v in an ordered array of integers a. <br>
If v appears in the array a, then the function returns an index i, such that a[i] == v; otherwise, -1 is returned.<br>
Assumption: the elements in the array a are sorted in non-decreasing order.<br>
```
int binarySearch(int v, int a[]){
  int lo,mid,hi;
  lo = 0;
  hi = a.length-1;
  while (lo <= hi){
    mid = (lo+hi)/2;
    if (v == a[mid])
      return (mid);
    else if (v < a[mid])
      hi = mid-1;
    else
      lo = mid+1;
  }
  return(-1);
}
```

**Equivalence Partitioning:**

| Tester Action and Input Data     | Expected Outcome      |
| ------------- | :---: |
| v is present in a        | Index of v         |
| v is not present in a         | -1         |

**Boundary Value Analysis:**

| Tester Action and Input Data     | Expected Outcome      |
| ------------- | :---: |
| Empty array a        | -1         |
| v is present at the first index of a         | 0         |
| v is present at the last index of a length of a        | -1         |
| v is not present in a         | -1         |

<br>

## Program 4:
P4. The following problem has been adapted from The Art of Software Testing, by G. Myers (1979). <br>
The function triangle takes three integer parameters that are interpreted as the lengths of the sides of a triangle. <br>
It returns whether the triangle is equilateral (three lengths equal), isosceles (two lengths equal), scalene (no lengths equal), or invalid (impossible lengths).<br>
```
final int EQUILATERAL = 0;
final int ISOSCELES = 1;
final int SCALENE = 2;
final int INVALID = 3;
int triangle(int a, int b, int c){
  if (a >= b+c || b >= a+c || c >= a+b)
    return(INVALID);
  if (a == b && b == c)
    return(EQUILATERAL);
  if (a == b || a == c || b == c)
    return(ISOSCELES);
  return(SCALENE);
}
```

**Equivalence Partitioning:**

| Tester Action and Input Data     | Expected Outcome      |
| ------------- | :---: |
| Invalid triangle (a+b<=c)        | INVALID         |
| Valid equilateral triangle (a=b=c)         | EQUILATERAL         |
| Valid isosceles triangle (a=b<c)        | ISOSCELES         |
| Valid scalene triangle (a<b<c)         | SCALENE         |

**Boundary Value Analysis:**

| Tester Action and Input Data     | Expected Outcome      |
| ------------- | :---: |
| Invalid triangle (a+b<=c)        | INVALID         |
| Invalid triangle (a+c<b)         | INVALID         |
| Invalid triangle (b+c<a)        | INVALID         |
| Valid equilateral triangle (a=b=c)         | EQUILATERAL         |
| Valid isosceles triangle (a=b<c)        | ISOSCELES         |
| Valid isosceles triangle (a=c<b)        | ISOSCELES         |
| Valid isosceles triangle (b=c<a)        | ISOSCELES         |
| Valid scalene triangle (a<b<c)         | SCALENE         |

<br>

## Program 5:
The function prefix (String s1, String s2) returns whether or not the string s1 is a prefix of string s2 (you may assume that neither s1 nor s2 is null).<br>
```
public static boolean prefix(String s1, String s2){
  if (s1.length() > s2.length()){
    return false;
  }
  for (int i = 0; i < s1.length(); i++){
    if (s1.charAt(i) != s2.charAt(i)){
      return false;
    }
  }
  return true;
}
```
**Equivalence Partitioning:**

| Tester Action and Input Data     | Expected Outcome      |
| ------------- | :---: |
| Empty string s1 and s2        | True         |
| Empty string s1 and non-empty s2         | True         |
| Non-empty s1 is a prefix of non-empty s2        | True         |
| Non-empty s1 is not a prefix of s2         | False         |
| Non-empty s1 is longer than s2         | False         |

**Boundary Value Analysis:**

| Tester Action and Input Data     | Expected Outcome      |
| ------------- | :---: |
| Empty string s1 and s2        | True         |
| Empty string s1 and non-empty s2         | True         |
| Non-empty s1 is not a prefix of s2         | False         |
| Non-empty s1 is longer than s2         | False         |
<br>

## Program 6:
Consider again the triangle classification program (P4) with a slightly different specification: <br>
The program reads floating values from the standard input. The three values A, B, and C are interpreted as representing the lengths of the sides of a triangle. <br>
The program then prints a message to the standard output that states whether the triangle, if it can be formed, is scalene, isosceles, equilateral, or right angled.<br>
Determine the following for the above program:<br>
<br>

**a) Identify the equivalence classes for the system<br>**

Equivalence Classes:<br>
EC1: All sides are positive, real numbers.<br>
EC2: One or more sides are negative or zero.<br>
EC3: The sum of the lengths of any two sides is less than or equal to the length of the remaining side (impossible lengths).<br>
EC4: The sum of the lengths of any two sides is greater than the length of the remaining side (possible lengths).<br>

<br>


**b) Identify test cases to cover the identified equivalence classes. Also, explicitly mention which test case would cover which equivalence class.<br>**
(Hint: you must need to be ensure that the identified set of test cases cover all identified equivalence classes)<br>

Test cases:<br>
TC1 (EC1): A=3, B=4, C=5 (right-angled triangle)<br>
TC2 (EC1): A=5, B=5, C=5 (equilateral triangle)<br>
TC3 (EC1): A=5, B=6, C=7 (scalene triangle)<br>
TC4 (EC1): A=5, B=5, C=7 (isosceles triangle)<br>
TC5 (EC2): A=-2, B=4, C=5 (invalid input)<br>
TC6 (EC2): A=0, B=4, C=5 (invalid input)<br>

<br>


**c) For the boundary condition A + B > C case (scalene triangle), identify test cases to verify the boundary.<br>**

Test cases for the boundary condition A + B > C:<br>
TC7 (EC4): A=2, B=3, C=6 (sum of A and B is equal to C)<br>

<br>


**d) For the boundary condition A = C case (isosceles triangle), identify test cases to verify the boundary.<br>**

Test cases for the boundary condition A = C:<br>
TC8 (EC4): A=5, B=6, C=5 (A equals to C)<br>

<br>

**e) For the boundary condition A = B = C case (equilateral triangle), identify test cases to verify the boundary.<br>**

Test cases for the boundary condition A = B = C:<br>
TC9 (EC4): A=1, B=1, C=1 (all sides are equal)<br>

<br>

**f) For the boundary condition A2 + B2 = C2 case (right-angle triangle), identify test cases to verify the boundary.<br>**

Test cases for the boundary condition A^2 + B^2 = C^2:<br>
TC10 (EC4): A=3, B=4, C=5 (right-angled triangle)<br>

<br>

**g) For the non-triangle case, identify test cases to explore the boundary.<br>**

Test cases for the non-triangle case:<br>
TC11 (EC3): A=2, B=2, C=4 (sum of A and B is less than C)<br>

<br>

**h) For non-positive input, identify test points.<br>**

Test points for non-positive input:<br>
TP1 (EC2): A=0, B=4, C=5 (invalid input)<br>
TP2 (EC2): A=-2, B=4, C=5 (invalid input)<br>
Note: Test cases TC1 to TC10 covers all identified equivalence classes.<br>

<br>


![Final](https://user-images.githubusercontent.com/62084382/231538537-89c3769c-1ee2-436b-8f1e-de80bd7ed551.png)
```
package lab_7;
public class unittesting {
	public int linearSearch(int v, int a[])
	{
		int i = 0;
		while (i < a.length)
		{
			if (a[i] == v)
				return(i);
			i++;
		}
		return (-1);
	}
	public int countItem(int v, int a[])
	{
		int count = 0;
		for (int i = 0; i < a.length; i++)
		{
			if (a[i] == v)
			count++;
	
		}
		return count;
	}
	
	public int binarySearch(int v, int a[])
	{
		int lo,mid,hi;
		lo = 0;
		hi = a.length-1;
		while (lo <= hi)
		{
			mid = (lo+hi)/2;
			if (v == a[mid])
				return (mid);
			else if (v < a[mid])
				hi = mid-1;
			else
				lo = mid+1;
		
		}
		return(-1);
	}
	
	public static String triangle(int a, int b, int c)
	{
		if (a >= b+c || b >= a+c || c >= a+b)
			return ("Incorrect input");
		if (a == b && b == c)
			return ("Equal");
		if (a == b || a == c || b == c)
			return ("Isosceles");
		return ("Scalene");
	}
	
	public static boolean prefix(String s1, String s2)
	{
		if (s1.length() > s2.length())
		{
			return false;
		}
		for (int i = 0; i < s1.length(); i++)
		{
			if (s1.charAt(i) != s2.charAt(i))
		{
				return false;
		}
		}
		return true;
	}
}
package lab_7;
import static org.junit.Assert.*;
import org.junit.Test;
public class LinaerSearch {
	@Test
	public void test() {
		unittesting obj = new unittesting();
       int[] arr1 = {2, 4, 6, 8, 10};
       int[] arr2 = {-3, 0, 3, 7, 11};
       int[] arr3 = {1, 3, 5, 7, 9};
      
       //assertEquals(2, obj.linearSearch(6, arr1));
       assertEquals(8, obj.linearSearch(3, arr2));
       assertEquals(4, obj.linearSearch(9, arr3));
	}
	
	@Test
	public void test2() {
		unittesting counter = new unittesting();
		int[] arr1 = {1, 2, 4, 4, 5};
		int[] arr2 = {1, 2, 3, 4, 5, 6, 7, 8, 9};
		int[] arr3 = {1, 2, 3, 4, 4, 4, 5, 6, 7, 8, 9};
		int v1 = 4;
		int v2 = 10;
		assertEquals(2, counter.countItem(v1, arr1));
		assertEquals(0, counter.countItem(v2, arr1));
		
	}
	
	@Test
	public void test3() {
		unittesting bs = new unittesting();
		
		int[] arr1 = {1, 3, 5, 7, 9};
		assertEquals(0, bs.binarySearch(1, arr1)); // search for 1 in {1, 3, 5, 7, 9}
		assertEquals(2, bs.binarySearch(5, arr1)); // search for 5 in {1, 3, 5, 7, 9}
		
		int[] arr2 = {2, 4, 6, 8, 10, 12};
		assertEquals(-1, bs.binarySearch(1, arr2)); // search for 1 in {2, 4, 6, 8, 10, 12}
		assertEquals(2, bs.binarySearch(6, arr2)); // search for 6 in {2, 4, 6, 8, 10, 12}
		
	}
	
	 @Test
	  public void testEquilateral() {
	    assertEquals("Equal", unittesting.triangle(3, 3, 3));
	  }
	  @Test
	  public void testIsosceles() {
	    assertEquals("Isosceles", unittesting.triangle(5, 5, 6));
	   
	  }
	  @Test
	  public void testScalene() {
	    assertEquals("Scalene", unittesting.triangle(3, 4, 5));
	  }
	  @Test
	  public void testIncorrectInput() {
	    assertEquals("Incorrect input", unittesting.triangle(1, 2, 3));
	   
	  }
	 
	  @Test
	    public void testPrefix() {
	        String s1 = "hello";
	        String s2 = "hello world";
	        assertTrue(unittesting.prefix(s1, s2));
	       
	        s1 = "abc";
	        s2 = "abcd";
	        assertTrue(unittesting.prefix(s1, s2));
	       
	        s1 = "";
	        s2 = "hello";
	        assertTrue(unittesting.prefix(s1, s2));
	       
	        s1 = "hello";
	        s2 = "hi";
	        assertFalse(unittesting.prefix(s1, s2));
	       
	        s1 = "abc";
	        s2 = "def";
	        assertFalse(unittesting.prefix(s1, s2));
	    }
	 
}

```

# **Section B**
1. **Control flow diagram:**<br>
![control-flow-diagram drawio](https://user-images.githubusercontent.com/75673068/231425222-27f0cc54-8a37-41a1-8d0f-b57b1db680a2.png)

2. **Test sets:**<br>

**a) Statement coverage test sets:** To achieve statement coverage, we need to make sure that every statement in the code is executed at least once.
<br>
* Test 1: p = empty vector
* Test 2: p = vector with one point
* Test 3: p = vector with two points with the same y component
* Test 4: p = vector with two points with different y components
* Test 5: p = vector with three or more points with different y components
* Test 6: p = vector with three or more points with the same y component

<br>

**b) Branch coverage test sets:** To achieve branch coverage, we need to make sure that every possible branch in the code is taken at least once
<br>
* Test 1: p = empty vector
* Test 2: p = vector with one point
* Test 3: p = vector with two points with the same y component
* Test 4: p = vector with two points with different y components
* Test 5: p = vector with three or more points with different y components, and none of them have the same x component
* Test 6: p = vector with three or more points with the same y component, and some of them have the same x component
* Test 7: p = vector with three or more points with the same y component, and all of them have the same x component

<br>

**c) Basic condition coverage test sets:** To achieve basic condition coverage, we need to make sure that every basic condition in the code (i.e., every Boolean subexpression) is evaluated as both true and false at least once
<br>
* Test 1: p = empty vector
* Test 2: p = vector with one point
* Test 3: p = vector with two points with the same y component, and the first point has a smaller x component
* Test 4: p = vector with two points with the same y component, and the second point has a smaller x component
* Test 5: p = vector with two points with different y components
* Test 6: p = vector with three or more points with different y components, and none of them have the same x component
* Test 7: p = vector with three or more points with the same y component, and some of them have the same x component
* Test 8: p = vector with three or more points with the same y component, and all of them have the same x component.





