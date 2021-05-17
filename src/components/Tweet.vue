<template>
  <div class="w-full p-4 border-b hover:bg-lighter flex">
    <div class="flex-none mr-4">
      <img src="https://pbs.twimg.com/profile_images/1311144185509146627/ekPPg1I3_400x400.jpg" class="h-12 w-12 rounded-full flex-none"/>
    </div>
    <div class="w-full">
      <div class="flex items-center w-full">
        <p class="font-semibold"> Lucas Bastos </p>
        <p class="text-sm text-dark ml-2"> @lucasbastos.dev </p>
        <p class="text-sm text-dark ml-2"> 1 sec </p>
        <i class="fas fa-angle-down text-dark ml-auto"></i>
      </div>
      <p class="py-2">
        {{ tweet.content }}
      </p>
      <div class="flex items-center justify-between w-full">
        <div class="flex items-center text-sm text-dark">
          <i class="far fa-comment mr-3"></i>
          <p> 0 </p>
        </div>
        <div class="flex items-center text-sm text-dark">
          <i class="fas fa-retweet mr-3"></i>
          <p> 0 </p>
        </div>
        <div class="flex items-center text-sm text-dark">
          <i class="fas fa-heart mr-3"></i>
          <p> 1 </p>
        </div>
        <div class="flex items-center text-sm text-dark">
          <i class="fas fa-share-square mr-3"></i>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Tweet',
  props: {
    tweet: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
