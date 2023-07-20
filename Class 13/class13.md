Today, we discussed the following topics:
Destructuring
The Spread Operator

Code we have written:
// Destructuring

const [a, h, b] = ["anas", "hassan", "basharat"]

const anas = students[0]
const hassan = students[1]
const basharat = students[2]

console.log(a, h, b)

console.log(students)

const {s1: goodS, s2, s3} = {s1: "Mubeen", s2: "Sufyan", s3: "Bilal"}

console.log(goodS)

// The Spread Operator

const teamStudents = ["Anas", "Hassan", "Bilal"]

const otherStudents = ["Mubeen", "Sufyan", "Basharat"]

const mergedStudents = [...teamStudents, ...otherStudents]

console.log(mergedStudents)

const user = {name:"aamuhammadi", age: "30"}

const userInfo = {
userName: "aam",
...user
}

console.log(userInfo)

const objRay = {name: "aamax",
services:
['seo', 'web', 'smm']}

console.log(objRay.services)

Today video link:
https://drive.google.com/file/d/1zFO0ZH2HBIvpCBLj_D6kz_yci6FjZXUU/view?usp=sharing
