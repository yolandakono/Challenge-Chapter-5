﻿# Challenge-Chapter-5
const express = require ("express")
const fs = require ("fs")
const app = express ()
const port= 4100; 
//MAAF BANGET KUMPULNYA TELAT KAK. pasti ganggu SCHEDULEnya banget, maaf ya kak
/*const database = require("./data/user.json")

!Gak tau kenapa ini gak jadi kak, terus bikin .env untuk portnya malah gak kebaca portnya dan di tulis "dotenv" not found!


app.use("./data" , express.static("./data"))

app.use(express.json())

app.post("/login", (req,res,next) => {
    try {
        const username = req.body.username
        const password = req.body.password

        const isExist = database.find(data => {
            return data.username === username
        })

        if (!isExist) {
            return res.login(404).json({
                message: "user tidak ditemukan"
            })
        }

        if (!isExist.password === password){
            return res.login(401).json({
                message: "wrong password"
            })
        }

        username.nap(user => {
            console.log(user)
        })

        return res.login(200).json({
            message : "Success"
        })
    }

})*/



app.use("/public",express.static("./public"));
app.get("/html",(req,res,next) => {
    const indexData = fs.readFileSync ("./public/WEBLAYOUT/chapter3.html")
    const data = indexData.toString()

    return res.status(200).contentType("html").send(data)
})

app.use("./public",express.static("./public"));
app.get("/byun",(req,res,next) => {
    const indexData = fs.readFileSync ("./public/Challenge 2/index.html")
    const data = indexData.toString()

    return res.status(200).contentType("html").send(data)
})

app.use("/data",express.static("./data"));
app.get("/json",(req,res,next) => {
    const jsonData = fs.readFileSync ("./data/user.json")
    const data = JSON.parse(jsonData.toString())

    return res.status(200).contentType("json").json(data)
})

app.listen(port, () => { 
    console.log(`connect to http://localhost:${port}`); 
});
