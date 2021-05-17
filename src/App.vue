<template>
  <div id="app" class="flex container h-screen w-full">
    <SideBar />
    <div class="w-full md:w-1/2 h-full overflow-y-scroll">
      <div class="px-5 py-3 border-b border-lighter flex items-center justify-between">
        <h1 class="text-xl font-bold">Página Inicial</h1>
        <i class="far fa-star text-xl text-blue"></i>
      </div>
      <div class="px-5 py-3 border-b-8 border-lighter flex">
        <div class="flex-none">
          <img src="https://pbs.twimg.com/profile_images/1311144185509146627/ekPPg1I3_400x400.jpg" class="flex-none w-12 h-12 rounded-full border border-lighter"/>
        </div>
        <form v-on:submit.prevent = "addNewTweet" class="w-full px-4 relative">
          <textarea v-model="tweet.content" placeholder="What's up?" class="mt-3 pb-3 w-full focus:outline-none"/>
          <div class="flex items-center">
            <i class="text-lg text-blue mr-4 far fa-image"></i>
            <i class="text-lg text-blue mr-4 fas fa-film"></i>
            <i class="text-lg text-blue mr-4 far fa-chart-bar"></i>
            <i class="text-lg text-blue mr-4 far fa-smile"></i>
          </div>
          <button type="submit" class="h-10 px-4 text-white font-semibold bg-blue hover:bg-darkblue focus:outline-none rounded-full absolute bottom-0 right-0">
            Tweet
          </button>
        </form>
      </div>
      <div class="flex flex-col-reverse">
        <div v-for="(tweet, index) in tweets" :key="index">
          <Tweet :tweet="tweet" />
        </div>
      </div>
      <div v-for="(follow, index) in following" :key="index">
        <Feed :follow="follow" />
      </div>
    </div>
    <!-- trending -->
    <div class="md:block hidden w-1/3 h-full border-l border-lighter py-2 px-6 overflow-y-scroll relative">
      <input class="pl-12 rounded-full w-full p-2 bg-lighter text-sm mb-4" placeholder="Buscar no Twitter" />
      <i class="fas fa-search absolute left-0 top-0 mt-5 ml-12 text-sm text-light"></i>
      <Trending :trending="trending" />
      <Recomended :friends="friends" />
    </div>
  </div>
</template>

<script>

import Tweet from '@/components/Tweet';
import Feed from '@/components/Feed';
import Recomended from '@/components/Recomended';
import SideBar from '@/components/SideBar.vue';
import Trending from '@/components/Trending.vue';

export default {
  name: 'app',
  components: {
    Tweet,
    Feed,
    Recomended,
    SideBar,
    Trending,
  },
  data() {
    return {
      id: '',
      dropdown: false,
      trending: [
        {top: 'Rio de Janeiro - Noite Anterior', title: 'Morre MC Kevin aos 23 anos; músico caiu da varanda de um hotel no Rio', bottom: ''},
        {top: 'Música', title: 'kevinho', bottom: 'Assuntos do Momento: #lutomckevin'},
        {top: 'Covid-19 - AO VIVO', title: 'Bahia: as últimas notícias sobre a pandemia', bottom: '40k tweets'},
      ],
      friends: [
        {src: 'https://pbs.twimg.com/profile_images/1206997998900850688/cTXTQiHm_400x400.jpg', name: 'Evan You', handle: '@youyuxi'},
        {src: 'https://pbs.twimg.com/profile_images/573984336271122432/k8vEBoCW_400x400.jpeg', name: 'Marvel', handle: '@Marvel:)'},
        {src: 'https://pbs.twimg.com/profile_images/1102364992/clean_code_72_color_400x400.png', name: 'Uncle Bob Martin', handle: '@unclebobmartin'}
      ],
      following: [
        {src: 'https://pbs.twimg.com/profile_images/1206997998900850688/cTXTQiHm_400x400.jpg', name: 'Evan You', handle: '@youyuxi', time: '20 min', tweet: "This Twitter clone looks better than the origin. @lucasbastos.dev is doing an amazing job!", comments: '1,481', retweets: '954', like: '5,040,103'},
        {src: 'https://pbs.twimg.com/profile_images/1206997998900850688/cTXTQiHm_400x400.jpg', name: 'Evan You', handle: '@youyuxi', time: '20 min', tweet: "Just got an SMS message asking me if I'm interested in a remote React job... I mean, how the hell did the recruiter got my number?", comments: '1,000', retweets: '550', like: '1,000,003'},
        {src: 'https://pbs.twimg.com/profile_images/1102364992/clean_code_72_color_400x400.png', name: 'Uncle Bob Martin', handle: '@unclebobmartin', time: '55 min', tweet: 'Advocates of a certain language or a certain paradigm sometimes claim that adherence automatically yields clean code. Sadly, this is never true. You can make a mess in any language or paradigm. Only discipline, care, and attention to detail can stave off the mess.', comments: '2,030', retweets: '50', like: '20,003'},
        {src: 'https://pbs.twimg.com/profile_images/1206997998900850688/cTXTQiHm_400x400.jpg', name: 'Evan You', handle: '@youyuxi', time: '1.4 hr', tweet: 'Haha just made a flame thrower. Shld I sell them?', comments: '100,000', retweets: '1,000,002', like: '5,000,003'},
        {src: 'https://pbs.twimg.com/profile_images/1206997998900850688/cTXTQiHm_400x400.jpg', name: 'Evan You', handle: '@youyuxi', time: '1.4 hr', tweet: 'Just did something crazyyyyyyy', comments: '100,500', retweets: '1,000,032', like: '5,000,103'}
      ],
      tweets: [
        {content: 'Tentando fazer um clone do Twitter'}
      ],
      tweet: {content: ''}
    }
  },
  methods: {
    addNewTweet () {
      let newTweet = {
        content: this.tweet.content
      };
      this.tweets.push (newTweet)
    }
  }
}
</script>
