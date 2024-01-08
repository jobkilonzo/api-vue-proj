<template>

    <table>
        <thead>
            <th class="li">Author</th>
            <th class="li">Content</th>
            <th class="li">Published</th>
            <th class="li">Lastly Updated</th>
        </thead>
        <tbody v-for="blog in blogs" :key="blog._id"  >
            <td class="li">{{ blog.author }}</td>
            <td class="li"> {{ blog.content }}</td>
            <td class="li">{{ blog.published }} </td>
            <td class="li">{{ blog.updatedAt }}</td>
        </tbody>
    </table>
</template>

<script setup>

const props = defineProps({
    blogs: {
        type: Array,
        required: true
    }
})
</script>