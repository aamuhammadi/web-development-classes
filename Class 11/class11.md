Today, we discussed the following topics:
Revisiting Operators
Revisiting Functions & Parameters
Arrow Functions
More on the Arrow Function Syntax

Code we have written:
console.log(10/5)

const message = "Asslamu Alaikum "
const name = "Irfan"

console.log(message + name)

console.log(5 === 5)

console.log(5 > 5)

function greet() {
console.log("asslamu alaikum");
}

greet();

function greetMe(name, message) {
console.log(name, message);
}

greetMe("AAM", "How Are You");

function greetMe(name, message = "How Are You") {
console.log(name, message);
}

greetMe("AAM");
greetMe("Hassan", "Ki hal e");

function greet() {
console.log("asslamu alaikum");
}

greet();

const greet = () => {
console.log("asslamu alaikum")
}

greet();

const name = () => console.log("asslamu alaikum")

name()

const greet = (message) => message

console.log(greet("How are you"))

const greet = message => message

console.log(greet("How are you"))

const greet = number => ({age: number})

console.log(greet(30))

const [message, setMessage] = useState("")

const greet = message => {
setMessage(message);
};

<h1>{message}</h1>
<button onClick={() => greet("Assalamu Alaikum")}>Click Me</button>

Today video link:
https://drive.google.com/file/d/17YTgLxH4CAGZaZ2Gk-9kZUo411ZGLgVR/view?usp=sharing
