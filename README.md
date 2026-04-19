trivia-cli/
│── package.json
│── index.js
{
"name": "trivia-cli",
"version": "1.0.0",
"description": "Simple Trivia CLI game",
"main": "index.js",
"type": "module",
"scripts": {
"start": "node index.js"
},
"dependencies": {
"inquirer": "^9.0.0",
"chalk": "^5.0.0"
}
}
import inquirer from "inquirer";
import chalk from "chalk";

// Questions
const questions = [
{
question: "What is the capital of France?",
choices: ["Berlin", "Madrid", "Paris", "Rome"],
answer: "Paris"
},
{
question: "Which language runs in a web browser?",
choices: ["Python", "Java", "C", "JavaScript"],
answer: "JavaScript"
},
{
question: "Who wrote 'Romeo and Juliet'?",
choices: ["Charles Dickens", "William Shakespeare", "Mark Twain", "Jane Austen"],
answer: "William Shakespeare"
}
];

// Game function
async function startGame() {
console.log(chalk.blue.bold("\n🎯 Welcome to Trivia CLI!\n"));

let score = 0;

for (const q of questions) {
const answer = await inquirer.prompt([
{
type: "list",
name: "userAnswer",
message: q.question,
choices: q.choices
}
]);

if (answer.userAnswer === q.answer) {
  console.log(chalk.green("✔ Correct!\n"));
  score++;
} else {
  console.log(chalk.red(`✖ Wrong! Correct answer: ${q.answer}\n`));
}

}

console.log(chalk.yellow(Your final score: ${score}/${questions.length}\n));
}

// Run game
startGame();
