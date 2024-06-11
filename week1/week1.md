# Week 1: Introduction to Machine Learning and Teachable Machine

This week, students will be introduced to the fundamental concepts of machine learning (ML) and get hands-on experience with Teachable Machine, a beginner-friendly tool for creating ML models. They will also learn about conditional logic using "if-else" statements.
## Objective:
- Define machine learning and understand its basic principles.
- Differentiate between supervised, unsupervised, and neural network learning.
- Build a simple image classification model using Teachable Machine.
- Grasp the concept of conditional logic using "if-else" statements in JavaScript.
- Hands-on with (teachablemachine)<https://teachablemachine.withgoogle.com/train/image>
## Activities:
### What is a if condition in python?
Conditional statements control the flow of execution based on certain conditions. In your project, these conditions are used to update the emoji displayed based on the class prediction from a machine learning model.
- if: This statement executes a block of code if the specified condition is true.
- else: This captures all other conditions that are not defined by the if or else if statements.
Example:
```
// When we get a result
function gotResult(error, results) {
  // Check for errors
  if (error) {
    console.error(error);
    return;
  }
  // Get the most confident prediction
  predictedClass = results[0].label;

  // Update the emoji based on the predicted class
  if (predictedClass === 'Thumbs Up') {
    myEmoji = "😁"; // Happy face for Thumbs Up
  }
  else {
    myEmoji = "❓"; // Question mark for any other or unknown predictions
  }
}
```
### Supprise! if-else
#### What is if-else? 
"else if" is used to specify a new condition to test if the first condition is false.
#### Why Use else if?
1. It allows for more nuanced decision-making in your code.
2. You can handle multiple specific cases (like different gestures) distinctly and appropriately.
```
// When we get a result
function gotResult(error, results) {
  // Check for errors
  if (error) {
    console.error(error);
    return;
  }
  // Get the most confident prediction
  predictedClass = results[0].label;

  // Update the emoji based on the predicted class
  if (predictedClass === 'Thumbs Up') {
    myEmoji = "😁"; // Happy face for Thumbs Up
  }
  # Here, after checking wether the emoji is 'Thumbs Up', we then check if it's 'Thumbs Down'
  else if (predictedClass === 'Thumbs Down') {
    myEmoji = "🙁"; // Sad face for Thumbs Down
  }
  else {
    myEmoji = "❓"; // Question mark for any other or unknown predictions
  }
}
```

### Introduction to basic ML concepts
#### What is machine learning?
- Machine Learning (ML): Algorithms that enable computers to learn from data. (Reference PDF page 3)
- Supervised Learning: Training a model with labeled data. (Reference PDF page 5)
- Unsupervised Learning: Finding patterns in data without labels. (Reference PDF page 5)
- Neural Networks: ML models inspired by the human brain. (Reference PDF page 5)
- If-Else Statements: Conditional logic
### Hands-on project with Teachable Machine to recognize simple gestures.
0. Grab yourself a forked version
	- Go to (replit)<https://replit.com/@nickianselmo/teachable-machine-p5-starter#index.html> and click the Fork&Run
	- Click on Fork Repl ToDo: take pictures
	- To the right, click script.js ToDo: take pictures
1. Train your own model
	- Go to (teachablemachine)<https://teachablemachine.withgoogle.com/train/image>
	- Change Class 1 to Thumbs Up
	- Change Class 2 to Thumbs Down
	- Click on Webcam under Thumbs Up and record materilas for Thumbs Up
	- Click on Webcam under Thumbs Down and record materilas for Thumbs Down
	
ToDo: take pictures
2. A simple swap
Change the 
ToDo: take pictures
3. Expand the If statement
The existing code classifies a video frame and updates an emoji based on whether the predicted class is 'Thumbs Up'.
 - Task:
	- Add an else if statement to handle the 'Thumbs Down' prediction.
## Supplement materials 
https://teachablemachine.withgoogle.com/train/image
https://replit.com/@nickianselmo/teachable-machine-p5-starter#index.html
