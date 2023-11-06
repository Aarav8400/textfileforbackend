# textfileforbackend

import express from "express";
import mongoose from "mongoose";
import bcrypt from 'bcrypt'
import jwt from "jsonwebtoken";
import userRouter from './routes/user.js'
const app=express()

app.use(express.json())

mongoose.connect("mongodb+srv://aarav123:rRJvBb6YcHBcfse4@blog.ugsvqdh.mongodb.net/",{
    dbName:"Blog"
}).then(()=>console.log("mongodb is connected"))



const userSchema=mongoose.Schema({
    name:{
        type:String,
        require:true
    },
    email:{
        type:String,
        require:true,
        unique:true
    },
    password:{
        type:String,
        require:true
    },
    createdAt:{
        type:Date,
        default:Date.now
    }
})

export const User=mongoose.model("User",userSchema)

app.use('/api/users',userRouter)


const port=4000;
app.listen(port,()=>{
    console.log(`server start on port: ${port}`);
})

___________________________________________________________________________________________________________________________________________________________________

MVC setup
model view controller
model banaye hai,utils banaye hai,controller banaye hai aur usme ode saare daal diye hai
