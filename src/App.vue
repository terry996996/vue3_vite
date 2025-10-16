<script>
import { ref } from 'vue'
import RefCourse from './components/RefCourse.vue';
import ReactiveCourse from './components/ReactiveCourse.vue';
import SplitCourse from './components/SplitCourse.vue';

export default{
components:{RefCourse, ReactiveCourse, SplitCourse},
 setup() {
    let userName = "KGI"
    let userNameRef = ref(userName)
    let count = 10
    let countRef = ref(count)
    let isOnline = false
    let isOnlineRef = ref(isOnline)
    console.log(typeof userNameRef, typeof userName) // object(RefImpl) string("KGI")
    console.log(userNameRef.value) // "KGI"
    // let courseRef = ref({
    //   courseName: "VUE",
    //   attendee: 10,
    //   isOnline: false
    // })
    // console.log("courseRef=", courseRef) // RefImpl
    // console.log("courseRef的值=",courseRef.value) // Proxy(Object)
    setTimeout(() => {
      // userNameRef.value = "ABC"
      userNameRef.value = "ABC"
      console.log("username=", userNameRef.value) // ABC
      countRef.value += 5
      isOnlineRef.value = !isOnlineRef.value


      //
      // courseRef.value.courseName = "Vue實戰"
      // courseRef.value.attendee += 5
      // courseRef.value.isOnline = true

      setTimeout(() => {
        userNameRef.value = "DEF"
        console.log("username=", userNameRef.value) // DEF
        countRef.value += 5
        isOnlineRef.value = !isOnlineRef.value
      }, 3000)
    }, 3000)
    return {
      userName: userNameRef, countRef: countRef,
      isOnline: isOnlineRef,
      //attendee:courseRef.value.attendee, // 不是響應式的
    }
  }
}
</script>

<template>
  <h1>pure value</h1>
  <h1>{{ userName }}</h1>
  <h2>{{ countRef }}</h2>
  <h3>{{ isOnline }}</h3>
  <hr />
  <RefCourse />
  <hr />
  <ReactiveCourse/>
  <hr />
  <SplitCourse />

</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>

