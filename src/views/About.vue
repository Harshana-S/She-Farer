<template>
  <div class="about">
  <nav class="header">
    <ul>
      <li><a href="">
        Log Out</a>
      </li>
    </ul>
  </nav>
  <Stepper/>
  </div>
</template>


<script>
// @ is an alias to /src
import Stepper from "@/components/Stepper.vue";

export default {
  name: "About",
  components: {
    Stepper,
  }
};
</script>

<style scoped>
.header{
  justify-items: right;
}
li{
list-style-type: none 
}
</style>
