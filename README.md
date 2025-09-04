# CSCI 1250 Lab 1: Solving Problems Like A Computer

## Learning Objectives
By the end of this lab, you will be able to:
- **Apply** computational thinking to real-world problems
- **Design** algorithms using pseudocode before implementing in C#
- **Create** simple models that represent real-world entities
- **Implement** decision-making structures in C# programs
- **Decompose** complex problems into manageable sub-problems
- **Recognize patterns** in programming solutions

---

## Setup and Review

### Quick Review: Last Week's Grade Calculator
Let's connect last week's work to today's computational thinking concepts:

1. **Decomposition**: We broke the grade calculation into parts (get inputs, calculate weights, display result)
2. **Pattern Recognition**: Each input followed the same pattern (prompt → input → convert)  
3. **Abstraction**: We focused only on grades, abstracted away from student names or course details
4. **Algorithm Design**: We created step-by-step instructions that became our code

### Today's Focus
We'll practice these skills with new problems and learn two additional concepts:
- **Pseudocode**: Planning our programs in plain English
- **Decision-Making**: Having our programs make choices based on conditions

# Phase 1: Pattern Recognition & Data Processing

## Scenario: Student Records Management
You work in the registrar's office and need to process student enrollment data. Let's identify patterns in how we handle similar data and create reusable solutions.

### Part A: Recognizing Data Patterns 
Look at these three different data processing tasks:

**Task 1: Calculate class size**
```csharp
cs1250Enrolled = 23
cs1100Enrolled = 31  
cs2020Enrolled = 18
totalStudents = cs1250Enrolled + cs1100Enrolled + cs2020Enrolled
```

**Task 2: Calculate average temperature**
```csharp
mondayTemp = 68
tuesdayTemp = 72
wednesdayTemp = 70
averageTemp = (mondayTemp + tuesdayTemp + wednesdayTemp) / 3
```

**Task 3: Calculate total study hours**
```csharp
mathHours = 4
scienceHours = 6
englishHours = 3
totalHours = mathHours + scienceHours + englishHours
```


### Part B: Creating Pattern Solutions

**Your Task**: Create `dataprocessor.cs` and implement the following functions. Focus on completing the calculation functions first, then use the provided helper functions.

**Functions for You to Complete**:

```csharp
float CalculateTotal(value1, value2, value3):
    // TODO: Calculate the total of the three values
    totalNumber = 0  # Replace this line with your calculation
    return totalNumber

float CalculateAverage(value1, value2, value3, data_type="float"):
    // TODO: Calculate the total first (hint: you can call calculate_total as a recursive function call)
    // TODO: Then calculate the average (total divided by 3)
    average = 0  // Replace this line with your calculation
    
    // This print statement is provided for you
    Console.WriteLine($"Average: {average}");
    return average
```

**Complete Functions Provided for You**:

```csharp
(float, float) ProcessCourseData() {
    Console.WriteLine("=== Course Enrollment Processor ===");

    Console.Write("Enter CSCI 1250 enrollment: ");
    float course1 = Convert.ToSingle(Console.ReadLine());
    Console.Write("Enter CSCI 1100 enrollment: ");
    float course2 = Convert.ToSingle(Console.ReadLine());
    Console.Write("Enter CSCI 2400 enrollment: ");
    float course3 = Convert.ToSingle(Console.ReadLine());

    float totalEnrolled = CalculateTotal(course1, course2, course3 );
    Console.WriteLine($"Total Enrolled: {totalEnrolled}");
    float avgClassSize = CalculateAverage(course1, course2, course3 );

    return (totalEnrolled, avgClassSize);
}

float ProcessTemperatureData()
{
    Console.WriteLine("\n=== Temperature Data Processor ===");

    Console.Write("Enter Monday temperature: ");
    float day1Temp = Convert.ToSingle(Console.ReadLine());
    Console.Write("Enter Tuesday temperature: ");
    float day2Temp = Convert.ToSingle(Console.ReadLine());
    Console.Write("Enter Wednesday temperature: ");
    float day3Temp = Convert.ToSingle(Console.ReadLine());
    
    float avgTemp = CalculateAverage(day1Temp, day2Temp, day3Temp);

    return avgTemp;
}

void Main() {
    // TODO: Call ProcessCourseData() and store the returned values
    // (float courseTotal, float courseAvg) = ProcessCourseData();
    
    // TODO: Call ProcessTemperatureData() and store the returned value  
    // float tempAvg = ProcessTemperatureData();
    
    Console.WriteLine("\n=== Summary Report ===");
    // TODO: Print summary information using the values you stored above
    // Console.WriteLine($"Total students across all courses: {courseTotal}");
    // Console.WriteLine($"Average class size: {courseAvg}");
    // Console.WriteLine($"Average temperature: {tempAvg}°F");
    Main();
}
```

**Your Tasks**:
1. **Complete `calculateTotal()`**: Add the three values together
2. **Complete `calculateAverage()`**: Calculate total, then divide by 3
3. **Complete `main()`**: Uncomment and complete the TODO sections

**Hints**:
- For `calculateAverage()`, you can reuse most of your `calculateTotal()` function
- The print statements and return statements are already provided
- Focus on the mathematical operations: addition and division

**Test Your Program**: 
Try these inputs to verify your functions work:
- Course enrollments: 23, 31, 18 (should total 72, average 24.0)
- Temperatures: 68.5, 72.0, 70.5 (should average 70.3)

---

# Phase 2: Algorithm Design with Pseudocode 

## Scenario: Academic Advisor Program
Design a program that acts like an academic advisor, helping students understand their grade status and what they need to improve.

### Part A: Understanding the Problem
Your advisor program should:
1. Calculate a student's current grade
2. Tell them what letter grade they have
3. If they're failing, suggest which assignments to focus on
4. Calculate what they need on the final project to reach their desired grade

### Part B: Algorithm Design in Pseudocode

Create a new file named `pseudocode.txt`. Write pseudocode for the academic advisor. Use these pseudocode conventions:

```
BEGIN ProgramName
    DISPLAY "message"
    READ variable
    SET variable = calculation
    IF condition THEN
        action
    ELSE
        different action
    END IF
END ProgramName
```

**Your Task**: Write complete pseudocode for the academic advisor program.

**Starter Template**:
```
BEGIN AcademicAdvisor
    DISPLAY "=== Academic Advisor ==="
    
    // Get current grades
    DISPLAY "Enter your exit tickets average: "
    READ exitTickets
    // Add more inputs...
    
    // Calculate current grade
    SET currentGrade = ...
    
    // Determine letter grade
    IF currentGrade >= 90 THEN
        SET letterGrade = "A"
    ELSE IF ...
        // Complete this logic
    END IF
    
    // Display current status
    DISPLAY "Your current grade is: currentGrade + letterGrade"
    
    // Add advisor suggestions...
    
END AcademicAdvisor
```

# Phase 3: Implementation with Decision-Making
*Create a new file: `academicAdvisor.cs`*

## Convert Your Pseudocode to C#
Now implement your academic advisor as a C# program.

### Part A: Basic Implementation
Create `academicAdvisor.cs` and translate your pseudocode to C#:

```csharp
string GetLetterGrade(float percentage) {
    if (percentage >= 90)
        return "A";
    else if (percentage >= 80)
        return "B";
    else if (percentage >= 70)
        return "C";
    else if (percentage >= 60)
        return "D";
    else
        return "F";
}

float CalculateCurrentGrade(float exitTickets, float quizzes, float labs, float finalProject) {
    // Your implementation here
    // Calculate weighted average - can reuse from the grade calculator lab
    
    return 0;
}

void Main()
{
    Console.WriteLine("=== Academic Advisor ===");
    
    // Get current grades from user input
    // Your code here
    
    // Calculate current grade from user input
    float currentGrade = CalculateCurrentGrade(exitTickets, quizzes, labs, finalProject);
    string letterGrade = GetLetterGrade(currentGrade);
    
    // Display current status
    Console.WriteLine($"Your current grade is: {currentGrade:F2}% ({letterGrade})");
    
    // Provide advice based on grade
    if (letterGrade == "F") {
        Console.WriteLine("You are currently failing. Consider:");
        Console.WriteLine("- Meeting with your professor during office hours");
        Console.WriteLine("- Focusing extra effort on upcoming assignments");
        Console.WriteLine("- Forming a study group with classmates");
    }
    else if (letterGrade == "D") {
        Console.WriteLine("You're passing but at risk. Consider:");
        Console.WriteLine("- Reviewing areas where you lost points");
        Console.WriteLine("- Asking for help on challenging topics");
    }
    else if (letterGrade == "C") {
        Console.WriteLine("✓ You're passing! To improve:");
        Console.WriteLine("- Review quiz mistakes for patterns");
        Console.WriteLine("- Start assignments earlier");
    }
    else if (letterGrade == "B") {
        Console.WriteLine("✓ Good work! You're doing well.");
        Console.WriteLine("- Keep up the consistent effort!");
    }
    else // A grade {
        Console.WriteLine("Excellent work! Keep it up!");
    }
}
```
**Test Output:**

Enter your Exit Ticket Average

85


Enter your Quizzes Average

80

Enter your Labs Average

90

Enter your Final Project Average

85

Your current grade is: 85, B
√ Good work! You're doing well.
Keep up the consistent effort!

---

# Submission Requirements

Submit all your C# files with proper documentation:
- [ ] `dataProcessor.cs` - Your code to calculate the totals and averages from Activity 2
- [ ] `academicAdvisor.cs` - Your complete academic advisor program  
- [ ] `pseudocode.txt` - Your pseudocode for the advisor program

**Code Requirements**:
- [ ] Code uses meaningful variable names
- [ ] Programs produce correct output for test cases
- [ ] Code is properly indented and readable


# Key Takeaways

Today you practiced computational thinking by:

- **Recognizing patterns** in code structure and reusing solutions through functions  
- **Creating abstractions** by focusing only on essential information in your models
- **Designing step-by-step algorithms** using pseudocode before coding
- **Making programs intelligent** through decision-making structures

These skills are fundamental to programming and problem-solving in computer science. Every complex system starts with these basic thinking patterns!

**Remember**: Professional programmers spend more time thinking about problems than typing code. The thinking skills you practiced today are what separate good programmers from great ones.

Credit: Original Python lab developed by Professor Ryan Haas, ETSU Dept. of Computing
