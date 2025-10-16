<template>
    <h1>ref for course object</h1>
    <p>{{ course }}</p>
    <p>course name:{{ course.courseName }}</p>
    <p>attendee:{{ course.attendee }}</p>
    <p>is online?{{ course.isOnline }}</p>
    <hr/>
    <h1>non reactive</h1>
    <p>course name:{{ courseName }}</p>
</template>

<script>
import { isReactive, isRef, ref } from 'vue';
export default {
    setup() {
        const course = {
            courseName: "VUE",
            attendee: 10,
            isOnline: false
        }
        const courseRef = ref(course)
        console.log("courseRef is ref?",isRef(courseRef)) // true
        console.log("courseRef is reactive?",isReactive(courseRef)) // false
        console.log("course is ref?",isRef(course)) // false
        console.log("course is reactive?",isReactive(course)) // false
        console.log("courseName is ref?",isRef(courseRef.value.courseName)) // false
        setTimeout(() => {
            courseRef.value.courseName = "Vue實戰"
            courseRef.value.attendee += 5
            courseRef.value.isOnline = true
        }, 1000)

        return { course: courseRef,
            courseName:courseRef.value.courseName
         }
    }
}
</script>

<style lang="scss" scoped></style>
