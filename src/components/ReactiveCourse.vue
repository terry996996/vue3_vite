<template>
    <h1>reactive for course object</h1>
    <p>{{ course }}</p>
    <p>course name:{{ course.courseName }}</p>
    <p>attendee:{{ course.attendee }}</p>
    <p>is online?{{ course.isOnline }}</p>
    <hr/>
    <h1>non reactive</h1>
    <p>{{ courseName }}</p>
</template>

<script>
import { isReactive, isRef, reactive } from 'vue';
export default {
    setup() {
        const course = reactive({
            courseName: "VUE",
            attendee: 10,
            isOnline: false
        })
        console.log("[reactive] course is ref?",isRef(course)) // false
        console.log("[reactive] course is ref?",isReactive(course)) // true
        console.log("[reactive] courseName is ref?",isRef(course.courseName)) // false
        console.log("[reactive] courseName is ref?",isReactive(course.courseName)) // false

        setTimeout(() => {
            course.courseName = "Vue實戰"
            course.attendee += 5
            course.isOnline = true
         }, 3000)
        return { course,courseName:course.courseName }
    }
}
</script>