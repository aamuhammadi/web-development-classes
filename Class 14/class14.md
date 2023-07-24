Today, we discussed the following topics:
Revisiting Control Structures
Using Functions as Values

Code we have written:
// Revisiting Control Structures
const password = prompt("Your Password");

if (password === "first") {
console.log("success on 1st")
} else if (password === "second"){
console.log("success on 2nd")
} else console.log("Access not granted")

const students = ["bilal", "mubeen", "basharat"]

for (const student of students) {
console.log(student)
}

for (let i = 1; i <= 10; i++){
console.log(i)
}

// Using Functions as Values
function fourSec () {
console.log("3 second")
}
function twoSec () {
console.log("2 second")
}
function oneSec () {
console.log("1 second")
}

setTimeout(fourSec, 3000)
setTimeout(twoSec, 2000)
setTimeout(oneSec, 1000)

setTimeout(()=>
console.log("5 second"), 5000)

Today video link:
https://drive.google.com/file/d/1diutK3kkAYJ3sQ3Pgg5qD-68HdbesJM5/view?usp=sharing
