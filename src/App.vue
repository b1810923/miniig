<template>
  <div id="app">
    <Menu :menu = header />
    <main>
      <Article :articles = article />
    </main>
    <Modal />
    <Toast />
  </div>
</template>

<script>
import '@/assets/css/reset.css'
import Menu from './components/Menu.vue'
import Article from './components/Article.vue'
import Toast from './components/Toast.vue'
import Modal from './components/Modal.vue'
import moment from 'moment'
export default {
  name: 'App',
  data() {
    return {
      header:[
        {
            title:'首頁',
            svg:'<svg aria-label="Home" fill="#262626" height="22" viewBox="0 0 48 48" width="22"><path d="M45.3 48H30c-.8 0-1.5-.7-1.5-1.5V34.2c0-2.6-2-4.6-4.6-4.6s-4.6 2-4.6 4.6v12.3c0 .8-.7 1.5-1.5 1.5H2.5c-.8 0-1.5-.7-1.5-1.5V23c0-.4.2-.8.4-1.1L22.9.4c.6-.6 1.5-.6 2.1 0l21.5 21.5c.4.4.6 1.1.3 1.6 0 .1-.1.1-.1.2v22.8c.1.8-.6 1.5-1.4 1.5zm-13.8-3h12.3V23.4L24 3.6l-20 20V45h12.3V34.2c0-4.3 3.3-7.6 7.6-7.6s7.6 3.3 7.6 7.6V45z"></path></svg>'
        },
        {
            title:'訊息',
            svg:'<svg aria-label="Direct" fill="#262626" height="22" viewBox="0 0 48 48" width="22"><path d="M46.5 3.5h-45C.6 3.5.2 4.6.8 5.2l16 15.8 5.5 22.8c.2.9 1.4 1 1.8.3L47.4 5c.4-.7-.1-1.5-.9-1.5zm-40.1 3h33.5L19.1 18c-.4.2-.9.1-1.2-.2L6.4 6.5zm17.7 31.8l-4-16.6c-.1-.4.1-.9.5-1.1L41.5 9 24.1 38.3z"></path><path d="M14.7 48.4l2.9-.7"></path></svg>'
        },
        {
            title:'探索',
            svg:'<svg aria-label="Find People" fill="#262626" height="24" viewBox="0 0 48 48" width="24"><path clip-rule="evenodd" d="M24 .5C37 .5 47.5 11 47.5 24S37 47.5 24 47.5.5 37 .5 24 11 .5 24 .5zm0 44c11.3 0 20.5-9.2 20.5-20.5S35.3 3.5 24 3.5 3.5 12.7 3.5 24 12.7 44.5 24 44.5zm-4.4-23.7c.3-.5.7-.9 1.2-1.2l14.8-8.1c.3-.1.6-.1.8.1.2.2.3.5.1.8l-8.1 14.8c-.3.5-.7.9-1.2 1.2l-14.8 8.1c-.3.1-.6.1-.8-.1-.2-.2-.3-.5-.1-.8l8.1-14.8zm6.2 5l4.3-7.8-7.8 4.3 3.5 3.5z" fill-rule="evenodd"></path></svg>'
        },
        {
            title:'珍藏',
            svg:'<svg aria-label="Activity Feed" fill="#262626" height="24" viewBox="0 0 48 48" width="24"><path clip-rule="evenodd" d="M34.3 3.5C27.2 3.5 24 8.8 24 8.8s-3.2-5.3-10.3-5.3C6.4 3.5.5 9.9.5 17.8s6.1 12.4 12.2 17.8c9.2 8.2 9.8 8.9 11.3 8.9s2.1-.7 11.3-8.9c6.2-5.5 12.2-10 12.2-17.8 0-7.9-5.9-14.3-13.2-14.3zm-1 29.8c-5.4 4.8-8.3 7.5-9.3 8.1-1-.7-4.6-3.9-9.3-8.1-5.5-4.9-11.2-9-11.2-15.6 0-6.2 4.6-11.3 10.2-11.3 4.1 0 6.3 2 7.9 4.2 3.6 5.1 1.2 5.1 4.8 0 1.6-2.2 3.8-4.2 7.9-4.2 5.6 0 10.2 5.1 10.2 11.3 0 6.7-5.7 10.8-11.2 15.6z" fill-rule="evenodd"></path></svg>'
        }    
      ],
      article:[]
    }
  },
  components: {
    Menu,
    Article,
    Toast,
    Modal
  },
  created(){
    let firstCard = new Object();
    firstCard.id = 1;
    firstCard.avatar = require("@/assets/avatar-01.jpg");
    firstCard.title ="wantogo";
    firstCard.place = "新竹尖石～6號花園";
    firstCard.img = require("@/assets/ig-01.jpg");
    firstCard.likebyimg = require("@/assets/liked-by01.jpg"); 
    firstCard.likeperson = "didiforu";
    firstCard.likecount = "117";
    firstCard.contenttitle = "taipeitravel";
    firstCard.content = "樂活公園櫻花接力盛開中，賞花GO🏃&zwj;♂<br>-<br>🌸2020樂活夜櫻季《樂櫻繽紛》🌸<br>📅日期：2/2~3/1<br>📍地點：內湖樂活公園(台北市內湖區康樂街61巷15弄)<br>🚌交通：公車路線：53、281、287區、630、646、903、藍51、棕19、內湖幹線、小1、小1區、通勤1A至東湖社區站<br>捷運路線：捷運東湖站<br>📍Attraction: Lohas Park<br>-----<br>♥感謝 <a class='mention'>@shadowjay</a>分享美照📷<br>-----<br>網美🐶!但牠是男生😅<br>&#65279;-----<br>"
    firstCard.comment = [
      {
        title:"changtingkang",
        mention: "@aom_indy",
        comment: "Taiwan is still ok though. I am pretty sure that now it’s one of the safest places in Asia."
      },
      {
        title:'aimue',
        mention:'@yuca524',
        comment:'明日は雪が降るんだって😍🙌お姉さんぽく見えるかね？見えないのもたくさんあるよ😂'
      }
    ]
    let fdatetime = '2020-03-12T10:28:56.000Z';
    let date = new Date(fdatetime);
    let fago = getTimeAgo(fdatetime);
    firstCard.datetime = fdatetime;
    firstCard.dateTitle = date.toUTCString();
    firstCard.dateAgo = `${fago} ago`;
    this.article.push(firstCard);

    let secondCard = new Object();
    secondCard.id = 2;
    secondCard.avatar = require("@/assets/avatar-02.jpg");
    secondCard.title = "yamakitatomoka";
    secondCard.place = "キャプション";
    secondCard.img = require("@/assets/ig-02.jpg");
    secondCard.likebyimg = require("@/assets/liked-by02.jpg");
    secondCard.likeperson = "chahen";
    secondCard.likecount = "316";
    secondCard.contenttitle = "yamakitatomoka";
    secondCard.content = ".<br>.<br>2019年の写活もこれで終わりかな？<br>.<br>今年もいろんなところ行ったなぁ。<br>カメラと娘がなかったらと思うとゾッとする。<br>.<br>来年の河津桜を楽しみに冬眠に入ります🥺🙏";
    secondCard.comment = [
      {
        title:"changtingkang",
        mention: "",
        comment: "紅葉に富士山にこはたんの後ろ姿…最高すぎます😭✨"
      },
      {
        title:'aimue',
        mention:'',
        comment:'わー😍ほんと素敵すぎです😍✨なんていうか、完璧！てかんじ✨✨✨'
      }
    ]
    let sdatetime = '2020-02-22T10:28:56.000Z';
    let sdate = new Date(sdatetime);
    let sago = getTimeAgo(sdatetime);
    secondCard.datetime = sdatetime;
    secondCard.dateTitle = sdate.toUTCString();
    secondCard.dateAgo = `${sago} ago`;
    this.article.push(secondCard);

    let thirdCard = new Object();
    thirdCard.id = 3;
    thirdCard.avatar = require("@/assets/avatar-03.jpg");
    thirdCard.title = 'visubal';
    thirdCard.place = 'London, United Kingdom';
    thirdCard.img = require("@/assets/ig-03.jpg");
    thirdCard.likebyimg = require("@/assets/liked-by03.jpg");
    thirdCard.likeperson = 'jia';
    thirdCard.likecount = '1945';
    thirdCard.contenttitle = 'visubal';
    thirdCard.content = 'Always love a good floral on black print. Inspired by <a class="hashtag">#richardquinn</a> SS20 worn by <a class="hashtag">#kendalljenner</a>, I use pressed roses and leaves to add depth and texture for my illustration of this beautiful gown. Have a great Friday my loves! <a class="hashtag">#lovelimzy</a> <a class="hashtag">#lovelimzyco</a>';
    thirdCard.comment = [
      {
        title:"changtingkang",
        mention: "",
        comment: "😍😍 WOW!  Beautiful work! 😍😍"
      },
      {
        title:'aimue',
        mention:'',
        comment:'Stunning artwork! So elegant!! 🌹❤️❤️'
      }
    ]
    let tdatetime = '2020-02-22T10:28:56.000Z';
    let tdate = new Date(tdatetime);
    let tago = getTimeAgo(tdatetime);
    thirdCard.datetime = tdatetime;
    thirdCard.dateTitle = tdate.toUTCString();
    thirdCard.dateAgo = `${tago} ago`;
    this.article.push(thirdCard);
  },
  mounted(){
    this.$bus.$on('lastId', (id)=>{
      let hasArticles = this.getArticles(id);
      if(!hasArticles){
        this.$bus.$emit('fetch' , false);
      }
    })
  },
  methods:{
    getArticles(lastArticleId) {
      fetch('https://lawch.org/fakeig?offsetId='+lastArticleId)
      .then((res)=>{
        return res.json()
      })
      .then((res)=>{
        if (res.length == 0){
          this.$bus.$emit('toastmsg', '已經顯示全部動態');
          return false;
        }else {
          let vm = this;      
          res.forEach(function(ele){
            let newArticle = new Object();
            newArticle.id = ele.id;
            newArticle.avatar = ele.author.profilePic;
            newArticle.title = ele.author.name;
            newArticle.place = ele.location;
            newArticle.img = ele.image;
            newArticle.likebyimg = ele.author.profilePic;
            newArticle.likeperson = '';
            newArticle.likecount = ele.likes;
            newArticle.contenttitle = ele.author.name;
            newArticle.content = ele.author.text;
            newArticle.comment = ele.comments.map(function(c){
              return {title:c.commenter,mention:'',comment:c.text}
            });
            newArticle.datetime = '2020-04-16T10:28:56.000Z';
            newArticle.dateTitle = new Date('2020-04-16T10:28:56.000Z').toUTCString();
            newArticle.dateAgo = ` ${getTimeAgo('2020-04-16T10:28:56.000Z')} ago`;
            vm.article.push(newArticle);
          });
          return true;
        }
      }).catch(()=>{
        this.$bus.$emit('toastmsg', '系統忙碌中，請稍後再試');
      })
    }
  }
}

function getTimeAgo(passtime) {
  return moment(passtime).toNow(true);
}
</script>

<style>
:root{
    --header-bg-color:#fff;
    --header-border-color: #dbdbdb;
    --tooltip-move: 11px;
    --tooltip-top-move: calc( calc(3.437rem - 22px) / 4);
    --tooltip-bg-color: #333;
    --tooltip-hover-color: #999;
    --times-text-color: #999;
    --page-bg-color: #fafafa;
    --card-bg-color: #fff;
    --common-border-color: #dbdbdb;
    --hashtag-text-color: #00356a;
}
body{
  font-size: 14px;
  line-height: 18px;
}
#app {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
main{
    margin-top: 3.437rem;
    padding-top: 60px;
    background-color: var(--page-bg-color);
}
</style>
