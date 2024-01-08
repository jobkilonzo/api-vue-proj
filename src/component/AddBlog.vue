<template>
<form id="form" class="form"  @submit.prevent="onSubmit">

    <div class="form-input">
        <label for="author">Author</label>
        <input class="input" type="text" id="author" v-model="author"/>
    </div>
    <div class="form-input">
        <label for="content">Content</label>
        <input class="input" type="text" id="content" v-model="content"/>
    </div>
    <div class="form-input">
        <label for="published">Published</label>
        <select class="input" id="published" v-model="published">
            <option value="false">False</option>
            <option value="true">True</option>
        </select>
    </div>

    <button class="input">Submit</button>
    
</form>
</template>

<script setup>
import {ref} from 'vue'

const author = ref('')
const content= ref('')
const published = ref('')

const emit = defineEmits(['blogSubmit'])
const onSubmit = () => {
    if(!author.value || !content.value || !published.value){
        return
    }
}

const blogData = {
    author: author.value,
    content: author.value,
    published: published.value
}

emit('blogSubmit', blogData)
</script>