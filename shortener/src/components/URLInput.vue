<script>
export default{
    data(){
        return {
            URLtext: ''
        }
    }
}
</script>

<template>
  <div class="URL_input">
    <h3>
      Input a URL
        <p>The original URL is: {{ URLtext }}</p>
        <p>The shortened URL is: {{ URLtext }}</p>
        <input v-model="URLtext" placeholder="Put in a URL" />
    </h3>
  </div>
</template>

<style scoped>
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}


@media (min-width: 1024px) {
  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
}
</style>
