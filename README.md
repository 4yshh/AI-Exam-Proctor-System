# AI Exam Proctor System

## Project Description
This project is an AI Exam Proctor System built in MIT App Inventor.
It allows students to take exams on mobile with a **60-second timer per question**.
Optional cheat detection monitors suspicious activity during the exam.

## Screens

# Screen1 – Login

**Purpose:**  
Screen1 allows the student to enter their Name and Student ID to start the exam. The data is stored in TinyDB for later use in the exam.



## Components & Palette Details

### 1. Label1 – Title
- **Palette:** User Interface → Label  
- **Drag & Drop:** Place at top of Screen1  
- **Properties:**
- **Purpose:** Display screen title.



### 2. TextBox1 – Student Name
- **Palette:** User Interface → TextBox  
- **Drag & Drop:** Below Label1  
- **Properties:**
- **Purpose:** Input field for student’s name.



### 3. TextBox2 – Student ID
- **Palette:** User Interface → TextBox  
- **Drag & Drop:** Below TextBox1  
- **Properties:**
- **Purpose:** Input field for student’s name.



- **Purpose:** Input field for student’s ID.



### 4. Button1 – Start Exam
- **Palette:** User Interface → Button  
- **Drag & Drop:** Below TextBox2  
- **Properties:**
- **Purpose:** Input field for student’s ID.



### 5. TinyDB1 – Store Student Data
- **Palette:** Storage → TinyDB  
- **Drag & Drop:** Anywhere on Screen1 (it will be invisible in the app)  
- **Properties / Setup:**
  - Tag: `"StudentName"` → stores student’s name
  - Tag: `"StudentID"` → stores student’s ID  
- **Purpose:** Keep student login info during the session.

- **Blocks Logic:**
```text
When Button1.Click:
  TinyDB1.StoreValue
      Tag: "StudentName"
      Value: TextBox1.Text
  TinyDB1.StoreValue
      Tag: "StudentID"
      Value: TextBox2.Text
  Open Screen2

### Screen2 – Exam
- LabelTimer: Countdown (60 seconds)
- Label1: Question text
- ListPicker1: Answer options (A, B, C, D)
- NextButton: Moves to next question
- Clock1: Timer logic

### Screen3 – Cheat Detection Engine (Optional)
- TinyDB1: Stores suspicious activity logs
- Clock1: Monitors user actions
- Notifier1: Shows alerts

### Screen4 – Dashboard / Results (Optional)
- Label: Exam Completed
- Label: Student Score
- ListView: Question-answer log
- Button: Back to Login

## Timer Logic (Screen2)
1. Initialize global variable `TimeLeft = 60`
2. Clock1.Timer:
    ```
    if TimeLeft > 0:
        TimeLeft = TimeLeft - 1
        LabelTimer.Text = TimeLeft
    else:
        ListPicker1.Enabled = false
        NextButton.Click
    ```
3. NextButton.Click:
    ```
    TimeLeft = 60
    ListPicker1.Enabled = true
    Clock1.TimerEnabled = true
    ```

