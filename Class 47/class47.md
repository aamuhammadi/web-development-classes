Today we have discussed the following topics:

Understanding Database Management in Strapi

Kindly find the video link below:
https://drive.google.com/file/d/1LNBaQKRNyIZ__oHOc1QRFidQtQSrO1IA/view?usp=sharing

Helpers code:

Must install this package in strapi to use postgresql
npm install pg –save

Code for Database file:

module.exports = ({ env }) => ({
connection: {
client: "postgres",
connection: {
host: env("DATABASE_HOST", "localhost"),
port: env.int("DATABASE_PORT", 5432),
database: env("DATABASE_NAME", "db-name"),
user: env("DATABASE_USERNAME", "postgres"),
password: env("DATABASE_PASSWORD", "password"),
ssl: env.bool("DATABASE_SSL", false) && {
key: env("DATABASE_SSL_KEY", undefined),
cert: env("DATABASE_SSL_CERT", undefined),
ca: env("DATABASE_SSL_CA", undefined),
capath: env("DATABASE_SSL_CAPATH", undefined),
cipher: env("DATABASE_SSL_CIPHER", undefined),
rejectUnauthorized: env.bool("DATABASE_SSL_REJECT_UNAUTHORIZED", true),
},
schema: env("DATABASE_SCHEMA", "public"),
},
pool: {
min: env.int("DATABASE_POOL_MIN", 2),
max: env.int("DATABASE_POOL_MAX", 10),
},
},
});
