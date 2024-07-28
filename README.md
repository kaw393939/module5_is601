# Module 5: Advanced OOP - Design Patterns and Logging in Python

## Module Overview
This module focuses on applying advanced object-oriented programming concepts, specifically the Command, Factory Method, and Observer design patterns, along with comprehensive logging practices. Students will refactor their CSV processor into a sophisticated, menu-driven command-line application, demonstrating their understanding of these advanced concepts and their ability to create maintainable, extensible software.

### Why Advanced OOP Concepts and Logging?
Advanced OOP concepts and design patterns allow for more flexible, maintainable, and extensible software design. Logging is crucial for debugging, monitoring, and maintaining applications. Understanding and applying these concepts is essential for creating professional-grade software and is highly valued in the software industry.

### Learning Outcomes
- Implement object-oriented programming principles in Python
- Develop a command-line application using the REPL pattern
- Apply professional program techniques such as DRY and Error handling using LBYL and EAFP
- Write and execute unit tests and integration tests for Python applications using pytest

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
     - Load CSV File
     - Display CSV Data
     - Sort CSV Data
     - Filter CSV Data
     - Generate HTML Report
     - Export CSV File
     - View Application Logs
     - Exit
2. **Implement the Command pattern:**
   - Create a separate command class for each menu option (e.g., `LoadCSVCommand`, `DisplayCSVCommand`, etc.)
   - Implement an abstract Command class with an `execute()` method
   - Create an Invoker class that stores and executes commands
3. **Use the Factory Method pattern:**
   - Implement a `CommandFactory` class that creates the appropriate Command objects
   - The factory should have a `create_command()` method that takes a command type and returns the corresponding Command object
4. **Implement the Observer pattern for file operations:**
   - Create a `FileOperationSubject` class that notifies registered observers when file operations (read/write) occur
   - Implement `FileOperationObserver` classes for logging and user notification
   - The Load CSV File and Export CSV File commands should use this system
5. **Add comprehensive logging:**
   - Use Python's logging module to log all significant events, including:
     - Application start and exit
     - All user actions and their results
     - File operations (read/write)
     - Errors and exceptions
   - Configure different logging levels (DEBUG, INFO, WARNING, ERROR)
   - Implement log rotation to manage log file sizes
   - The View Application Logs option should display recent log entries
6. **Error Handling:**
   - Implement robust error handling throughout the application
   - Log all exceptions and display user-friendly error messages
7. **Testing:**
   - Write unit tests for all major components, including:
     - Individual Command classes
     - CommandFactory class
     - FileOperationSubject and Observer classes
     - Logging functionality
   - Implement integration tests to ensure proper interaction between components
8. **Documentation:**
   - Provide clear, comprehensive documentation of the application's design, including:
     - UML class diagram showing the relationships between classes
     - Explanation of how each design pattern is used in the application
     - Instructions for running the application and tests
9. **Code Quality:**
   - Follow PEP 8 style guidelines
   - Use meaningful variable and function names
   - Include appropriate comments and docstrings
10. **Version Control:**
    - Use Git for version control, with meaningful commit messages
    - Configure GitHub Actions to run tests automatically on each push

**Grading Expectations:**
- Correct implementation of the Command pattern for menu options
- Proper use of the Factory Method pattern for command creation
- Effective implementation of the Observer pattern for file operation notifications
- Comprehensive and well-structured logging throughout the application
- User-friendly menu-driven interface with all specified options functional
- Robust error handling and logging of exceptions
- Thorough unit and integration tests with high code coverage
- Clear, comprehensive documentation including UML diagrams
- Adherence to Python best practices and PEP 8 style guidelines
- Successful GitHub Actions runs demonstrating passing tests

**Alignment:**
- Implement object-oriented programming principles in Python
- Develop a command-line application using the REPL pattern
- Apply professional program techniques such as DRY and Error handling using LBYL and EAFP
- Write and execute unit tests and integration tests for Python applications using pytest

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
   - Identifying appropriate use cases for each design pattern
   - Understanding the relationships between components in each pattern
   - Best practices for implementing logging in Python applications
   - Recognizing code smells that suggest the need for refactoring using design patterns
4. Review all provided materials, including cheat sheets, tutorials, and your refactored project code before taking the quiz.
5. The quiz will include multiple-choice, short answer, and code analysis questions to evaluate your comprehension of advanced OOP concepts, design patterns, and logging practices in Python.
