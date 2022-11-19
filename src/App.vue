<template>
  <ul>
    <li>
        <learning-resouce v-for="res in storedResources" :key="res.id"
            :title="res.title" :description="res.description" :link="res.link">
        </learning-resouce>
    </li>
  </ul>
</template>

<script>
import LearningResouce from './components/learningResources/LearningResource.vue';

export default {
    components: {
        LearningResouce
    },
    data() {
        return {
            storedResources: [
                { 
                    id: 'official-guide',
                    title: 'Official Guide',
                    description: 'The official Vue.js documentation',
                    link: 'https://vuejs.org'
                },
                { 
                    id: 'google',
                    title: 'Google',
                    description: 'Well, it\'s Google!',
                    link: 'https://google.com'
                }
            ]
        }
    }
}
</script>

<style>

</style>