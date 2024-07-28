# Module 5: Advanced OOP - Design Patterns and Logging in Python

## Module Overview
This module focuses on applying advanced object-oriented programming concepts, specifically the Command, Factory Method, and Observer design patterns, along with comprehensive logging practices. Students will refactor their CSV processor into a sophisticated, menu-driven command-line application, demonstrating their understanding of these advanced concepts and their ability to create maintainable, extensible software.

### Why Advanced OOP Concepts and Logging?
Advanced OOP concepts and design patterns allow for more flexible, maintainable, and extensible software design. Logging is crucial for debugging, monitoring, and maintaining applications. Understanding and applying these concepts is essential for creating professional-grade software and is highly valued in the software industry.

### Learning Outcomes
- Implement object-oriented programming principles in Python.
- Develop a command-line application using the REPL pattern.
- Apply professional program techniques such as DRY and Error handling using LBYL and EAFP.
- Write and execute unit tests and integration tests for Python applications using pytest.

## Module 5 Learning Pathway

### Recall
**Title:** Review of Basic OOP Concepts and Introduction to Design Patterns  
**Grading Type:** Points  
**Instructions:**
1. Participate in a discussion forum about your experiences with basic OOP concepts.
2. Share any familiarity with design patterns or logging in Python.
3. Complete a brief quiz on basic OOP concepts and simple design patterns.

### Read
**Article:** [Command Pattern in Python](https://refactoring.guru/design-patterns/command/python/example)  
**Purpose:** To understand and learn to implement the Command pattern in Python.

**Article:** [Factory Method Pattern in Python](https://refactoring.guru/design-patterns/factory-method/python/example)  
**Purpose:** To learn about the Factory Method pattern for flexible object creation.

**Article:** [Observer Pattern in Python](https://refactoring.guru/design-patterns/observer/python/example)  
**Purpose:** To explore the Observer pattern for event handling in applications.

**Article:** [Logging in Python](https://realpython.com/python-logging/)  
**Purpose:** To learn about Python's logging module and best practices.

**Article:** [Creating Command-Line Interfaces in Python](https://realpython.com/command-line-interfaces-python-argparse/)  
**Purpose:** To understand how to create robust command-line interfaces.

### Watch
**Video:** [Implementing Design Patterns in Python](https://www.youtube.com/watch?v=VVFBu-DYS_A) (30 minutes)  
**Purpose:** To provide practical demonstrations of Command, Factory Method, and Observer pattern implementations.

**Video:** [Effective Logging Practices in Python](https://www.youtube.com/watch?v=YmpChvYbN0I) (15 minutes)  
**Purpose:** To showcase best practices for logging in Python applications.

**Video:** [Designing Menu-Driven Command-Line Interfaces](https://www.youtube.com/watch?v=-drC1uL99iw) (20 minutes)  
**Purpose:** To demonstrate techniques for creating user-friendly command-line menus.

### Review
**Resource:** [Python Design Patterns Cheat Sheet](https://refactoring.guru/design-patterns)  
**Purpose:** To provide a quick reference for common design patterns in Python.

**Resource:** [Python Logging Cheat Sheet](https://www.splunk.com/en_us/blog/tips-and-tricks/python-logging-best-practices-tips.html)  
**Purpose:** To offer a concise guide for Python's logging module.

### Submit
**Activity Type:** Advanced OOP and Logging Implementation Assignment  
**Activity Title:** Advanced CSV Processor: A Command-Line Application with Design Patterns and Logging  
**Grading Type:** Points  
**Submission Instructions:** Submit a link to your GitHub repository containing the refactored project.  
**Instructions:**
1. Refactor your CSV Processor into a menu-driven command-line application that demonstrates the use of the Command, Factory Method, and Observer patterns, along with comprehensive logging. The application should provide the following functionality:
   - **Main Menu:**
     - **Load CSV File:** Load a CSV file into the application. This should trigger file reading operations and notify observers about the file load event.
     - **Display CSV Data:** Show the content of the loaded CSV file in a readable format.
     - **Sort CSV Data:** Allow users to sort the CSV data based on selected columns.
     - **Filter CSV Data:** Enable filtering of CSV data based on user-defined criteria.
     - **Generate HTML Report:** Create an HTML report from the CSV data.
     - **Export CSV File:** Export the current state of the CSV data to a new file. Notify observers about the file write event.
     - **View Application Logs:** Display recent log entries from the logging system.
     - **Exit:** Exit the application gracefully.

2. **Implement the Command pattern:**
   - Create a separate command class for each menu option (e.g., `LoadCSVCommand`, `DisplayCSVCommand`, etc.).
   - Implement an abstract `Command` class with an `execute()` method.
   - Create an `Invoker` class that stores and executes commands.
   - **Example:**
     ```python
     class Command:
         def execute(self):
             pass

     class LoadCSVCommand(Command):
         def __init__(self, receiver):
             self.receiver = receiver

         def execute(self):
             self.receiver.load_csv()

     class Invoker:
         def __init__(self):
             self.commands = {}

         def register(self, command_name, command):
             self.commands[command_name] = command

         def execute(self, command_name):
             if command_name in self.commands:
                 self.commands[command_name].execute()
     ```

3. **Use the Factory Method pattern:**
   - Implement a `CommandFactory` class that creates the appropriate Command objects.
   - The factory should have a `create_command()` method that takes a command type and returns the corresponding Command object.
   - **Example:**
     ```python
     class CommandFactory:
         @staticmethod
         def create_command(command_type, receiver):
             if command_type == 'load_csv':
                 return LoadCSVCommand(receiver)
             elif command_type == 'display_csv':
                 return DisplayCSVCommand(receiver)
             # Add other command types here
             else:
                 return None
     ```

4. **Implement the Observer pattern for file operations:**
   - Create a `FileOperationSubject` class that notifies registered observers when file operations (read/write) occur.
   - Implement `FileOperationObserver` classes for logging and user notification.
   - **Example:**
     ```python
     class FileOperationSubject:
         def __init__(self):
             self._observers = []

         def register_observer(self, observer):
             self._observers.append(observer)

         def notify_observers(self, event):
             for observer in self._observers:
                 observer.update(event)

     class FileOperationObserver:
         def update(self, event):
             pass

     class LoggingObserver(FileOperationObserver):
         def update(self, event):
             logging.info(f"File operation event: {event}")
     ```

5. **Add comprehensive logging:**
   - Use Python's logging module to log all significant events, including:
     - Application start and exit
     - All user actions and their results
     - File operations (read/write)
     - Errors and exceptions
   - Configure different logging levels (DEBUG, INFO, WARNING, ERROR)
   - Implement log rotation to manage log file sizes
   - The View Application Logs option should display recent log entries
   - **Example:**
     ```python
     import logging

     logging.basicConfig(level=logging.INFO,
                         format='%(asctime)s - %(name)s - %(levelname)s - %(message)s',
                         handlers=[logging.FileHandler('app.log', maxBytes=2000, backupCount=5)])

     logging.info('Application started')
     ```

6. **Error Handling:**
   - Implement robust error handling throughout the application.
   - Log all exceptions and display user-friendly error messages.
   - **Look Before You Leap (LBYL) Example:**
     ```python
     if os.path.exists('file.csv'):
         with open('file.csv', 'r') as file:
             data = file.read()
     else:
         print("File does not exist")
     ```
   - **Easier to Ask Forgiveness than Permission (EAFP) Example:**
     ```python
     try:
         with open('file.csv', 'r') as file:
             data = file.read()
     except FileNotFoundError:
         print("File does not exist")
     ```

7. **HTML Report:**
   - The HTML report should include:
     - A summary of the CSV data, including the number of rows and columns.
     - A table displaying the CSV data.
     - Visual representations (e.g., charts) of key data insights, if applicable.
   - **Example using pandas and matplotlib:**
     ```python
     import pandas as pd
     import matplotlib.pyplot as plt

     df = pd.read_csv('file.csv')

     # Generate HTML table
     html_table = df.to_html()

     # Plot data
     plt.figure(figsize=(10, 6))
     df['column_name'].value_counts().plot(kind='bar')
     plt.savefig('plot.png')

     # Create HTML report
     with open('report.html', 'w') as file:
         file.write(f"<html><body>{html_table}<img src='plot.png'></body></html>")
     ```

8. **Sorting and Filtering:**
   - Implement sorting and filtering functionality using pandas.
   - **Sorting Example:**
     ```python
     sorted_df = df.sort_values(by='column_name')
     ```
   - **Filtering Example:**
     ```python
     filtered_df = df[df['column_name'] == 'value']
     ```

9. **Recommended Python Packages:**
   - `pandas` for data manipulation
   - `argparse` for command-line argument parsing
   - `logging` for logging
   - `pytest` for testing
   - `matplotlib` for plotting
   - `jinja2` for HTML templating

10. **Example CSV File:**
    ```csv
    Name, Age, Occupation
    Alice, 28, Engineer
    Bob, 34, Data Scientist
    Carol, 45, Manager
    Dave, 23, Intern
    Eve, 38, Designer
    ```

### Grading Expectations:
- Correct implementation of the Command pattern for menu options.
- Proper use of the Factory Method pattern for command creation.
- Effective implementation of the Observer pattern for file operation notifications.
- Comprehensive and well-structured logging throughout the application.
- User-friendly menu-driven interface with all specified options functional.
- Robust error handling and logging of exceptions.
- Thorough unit and integration tests with high code coverage.
- Clear, comprehensive documentation including UML diagrams.
- Adherence to Python best practices and PEP 8 style guidelines.
- Successful GitHub Actions runs demonstrating passing tests.

### Reflect
**Title:** Module 5 Advanced OOP, Design Patterns, and Logging Reflection  
**Grading Type:** Points  
**Instructions:**
1. Write a comprehensive reflection (600-700 words) on your experience refactoring the CSV processor into an advanced command-line application.
2. Discuss the benefits and challenges of implementing each design pattern (Command, Factory Method, Observer).
3. Analyze how the addition of logging improved your development process and application maintainability.
4. Reflect on the differences between your original code and the refactored version in terms of flexibility, maintainability, and user experience.
5. Discuss how the use of design patterns and advanced OOP concepts might benefit larger software projects.
6. Identify areas where you feel you've grown most in your understanding of advanced OOP and software design principles.
7. Describe any difficulties you encountered during the refactoring process and how you overcame them.

### Quiz
**Title:** Advanced OOP, Design Patterns, and Logging Quiz  
**Grading Type:** Points  
**Instructions:**
1. Complete a comprehensive quiz covering the Command pattern, Factory Method pattern, Observer pattern, and logging in Python.
2. The quiz will assess your understanding of when and how to apply these patterns and logging practices.
3. It will include questions on:
   - Identifying appropriate use cases for each design pattern.
   - Understanding the relationships between components in each pattern.
   - Best practices for implementing logging in Python applications.
   - Recognizing code smells that suggest the need for refactoring using design patterns.
4. Review all provided materials, including cheat sheets, tutorials, and your refactored project code before taking the quiz.
5. The quiz will include multiple-choice, short answer, and code analysis questions to evaluate your comprehension of advanced OOP concepts, design patterns, and logging practices in Python.
