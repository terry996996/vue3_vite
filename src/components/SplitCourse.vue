<!-- <template>
    <div>
        <h1>destruct reactive object</h1>
        <h1>reactive for course object</h1>
        <p>{{ course }}</p>
        <p>course name:{{ course.courseName }}</p>
        <p>attendee:{{ course.attendee }}</p>
        <p>is online?{{ course.isOnline }}</p>
        <hr />
        <h1>refs會跟著變的</h1>
        <p>{{ courseName }}</p>
        <p>{{ attendee }}</p>
        <p>{{ isOnline }}</p>
    </div>
</template>

<script>
import { reactive, toRef, toRefs } from 'vue';
export default {
    setup() {
        const course = reactive({
            courseName: "VUE",
            attendee: 10,
            isOnline: false
        })

        const { courseName, attendee, isOnline } = course
        console.log(courseName, attendee, isOnline)
        const x = toRefs(course)
        //const {courseName, attendee, isOnline} = toRefs(course)
        console.log(x.courseName, x.attendee, x.isOnline)
        setTimeout(() => {
            course.courseName = "Vue實戰"
            course.attendee += 5
            course.isOnline = true
            setTimeout(() => { 
                x.courseName.value="Vue full stack 實戰"
                x.attendee.value += 20
                x.isOnline.value = false
            }, 3000)
        }, 3000)

        //return { course, courseName, attendee, isOnline }
        return { course, ...toRefs(course) }
    }
}
</script> -->


<template>
    <div>
        <h1>destruct reactive object</h1>
        <h1>reactive for course object</h1>
        <p>{{ course }}</p>
        <p>course name:{{ courseName }}</p>
        <p>attendee:{{ attendee }}</p>
        <p>is online?{{ isOnline }}</p>
    </div>
</template>

<script>
import { reactive, toRefs, toRef } from 'vue';
export default {
    setup() {
        const course = reactive({
            courseName: "VUE",
            attendee: 10,
            isOnline: false
        })

        // const { courseName, attendee, isOnline } = toRefs(course)
        // 另一種寫法 分開解構賦值 並分次搭配toRef
        const courseName = toRef(course, 'courseName')
        const attendee = toRef(course, 'attendee')
        const isOnline = toRef(course, 'isOnline')

        
        setTimeout(() => {
            course.courseName = "Vue實戰"
            course.attendee += 5
            course.isOnline = true
            setTimeout(() => { 
                courseName.value="Vue full stack 實戰"
                attendee.value += 20
                isOnline.value = false
            }, 3000)
        }, 3000)

        return { course, courseName, attendee, isOnline }
    }
}
</script>