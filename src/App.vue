<template>
    <Header/>
    <Blogs :blogs="blogs"/>
    <AddBlog @blogSubmit="handleSubmit"/>
</template>

<script setup>
import Header from './component/Header.vue'
import Blogs from './component/Blogs.vue';
import { onMounted, ref } from 'vue';
import AddBlog from './component/AddBlog.vue';

const blogs = ref([])

const fetchBlogs = async () =>{
   try{
    const res = await fetch('http://localhost:4001/api/blog', {
        method: "GET"
    })
    const data = await res.json()
    blogs.value  = data
    
   }catch(err){
    console.log(err)
   }
}
const AddBlogs = async () =>{
   try{
    const res = await fetch('http://localhost:4001/api/blog', {
        method: "POST",
        headers: {
                "content-type": "application/json"
        },
        credentials: 'include',
        body: JSON.stringify(blogs)
    })
    const data = await res.json()

    console.log(data.data)
    
    
   }catch(err){
    console.log(err)
   }
}

onMounted(()=>{
    fetchBlogs()
})
const handleSubmit = ()=> {
    AddBlogs()
}
</script>