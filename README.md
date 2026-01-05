# AI Exam Proctor System

## Project Description
This project is an AI Exam Proctor System built in MIT App Inventor.
It allows students to take exams on mobile with a **60-second timer per question**.
Optional cheat detection monitors suspicious activity during the exam.

## Screens

### Screen1 – Login
- Label: Student Login
- TextBox1: Enter Name
- TextBox2: Enter Student ID
- Button1: Start Exam
- TinyDB1: Stores student info

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

## Folder Structure

