<template>
    <div class="card-list">
    <article class="card-wrapper" :data-id="article.id" :data-index="index" :key="index" v-for="(article,index) in articles">
        <div class="header">
            <div class="avatar">
                <img :src="article.avatar" width="100%" />
            </div>
            <div class="desc">
                <div class="title">{{article.title}}</div>
                <div class="place">{{article.place}}</div>
            </div>
            <div class="options" data-name="options" @click="showModal">
                <svg aria-label="More options" fill="#262626" height="16" viewBox="0 0 48 48" width="16">
                    <circle clip-rule="evenodd" cx="8" cy="24" fill-rule="evenodd" r="4.5"></circle>
                    <circle clip-rule="evenodd" cx="24" cy="24" fill-rule="evenodd" r="4.5"></circle>
                    <circle clip-rule="evenodd" cx="40" cy="24" fill-rule="evenodd" r="4.5"></circle>
                </svg>
            </div>
        </div>
        <div class="img">
            <img :src="article.img" width="100%" />
        </div>
        <div class="actions">
            <button data-name="buttonLike" @click="btnLike">
                <svg aria-label="Like" fill="#262626" height="24" viewBox="0 0 48 48" width="24">
                    <path clip-rule="evenodd"
                        d="M34.3 3.5C27.2 3.5 24 8.8 24 8.8s-3.2-5.3-10.3-5.3C6.4 3.5.5 9.9.5 17.8s6.1 12.4 12.2 17.8c9.2 8.2 9.8 8.9 11.3 8.9s2.1-.7 11.3-8.9c6.2-5.5 12.2-10 12.2-17.8 0-7.9-5.9-14.3-13.2-14.3zm-1 29.8c-5.4 4.8-8.3 7.5-9.3 8.1-1-.7-4.6-3.9-9.3-8.1-5.5-4.9-11.2-9-11.2-15.6 0-6.2 4.6-11.3 10.2-11.3 4.1 0 6.3 2 7.9 4.2 3.6 5.1 1.2 5.1 4.8 0 1.6-2.2 3.8-4.2 7.9-4.2 5.6 0 10.2 5.1 10.2 11.3 0 6.7-5.7 10.8-11.2 15.6z"
                        fill-rule="evenodd"></path>
                </svg>
            </button>
            <button data-name="buttonComment" @click="btnComment"> 
                <svg aria-label="Comment" fill="#262626" height="24" viewBox="0 0 48 48" width="24">
                    <path clip-rule="evenodd"
                        d="M47.5 46.1l-2.8-11c1.8-3.3 2.8-7.1 2.8-11.1C47.5 11 37 .5 24 .5S.5 11 .5 24 11 47.5 24 47.5c4 0 7.8-1 11.1-2.8l11 2.8c.8.2 1.6-.6 1.4-1.4zm-3-22.1c0 4-1 7-2.6 10-.2.4-.3.9-.2 1.4l2.1 8.4-8.3-2.1c-.5-.1-1-.1-1.4.2-1.8 1-5.2 2.6-10 2.6-11.4 0-20.6-9.2-20.6-20.5S12.7 3.5 24 3.5 44.5 12.7 44.5 24z"
                        fill-rule="evenodd"></path>
                </svg>
            </button>
            <button data-name="buttonShare" @click="btnShare">
                <svg aria-label="Share Post" fill="#262626" height="24" viewBox="0 0 48 48" width="24">
                    <path
                        d="M46.5 3.5h-45C.6 3.5.2 4.6.8 5.2l16 15.8 5.5 22.8c.2.9 1.4 1 1.8.3L47.4 5c.4-.7-.1-1.5-.9-1.5zm-40.1 3h33.5L19.1 18c-.4.2-.9.1-1.2-.2L6.4 6.5zm17.7 31.8l-4-16.6c-.1-.4.1-.9.5-1.1L41.5 9 24.1 38.3z">
                    </path>
                    <path d="M14.7 48.4l2.9-.7"></path>
                </svg>
            </button>
            <button>
                <svg aria-label="Save" class="_8-yf5 " fill="#262626" height="24" viewBox="0 0 48 48" width="24">
                    <path
                        d="M43.5 48c-.4 0-.8-.2-1.1-.4L24 29 5.6 47.6c-.4.4-1.1.6-1.6.3-.6-.2-1-.8-1-1.4v-45C3 .7 3.7 0 4.5 0h39c.8 0 1.5.7 1.5 1.5v45c0 .6-.4 1.2-.9 1.4-.2.1-.4.1-.6.1zM24 26c.8 0 1.6.3 2.2.9l15.8 16V3H6v39.9l15.8-16c.6-.6 1.4-.9 2.2-.9z">
                    </path>
                </svg>
            </button>

        </div>
        <div class="bottom">
            <section class="likes">
                <div class="liked-by"><img :src="article.likebyimg" width="100%" /></div>Liked by
                <a>{{article.likeperson}}</a> and <a><span class="liked-count" data-name="likesCount">{{article.likecount}}</span> others</a>
            </section>
            <section class="content">
                <a :title="article.contenttitle">{{article.contenttitle}}</a>&nbsp;
                <span v-html=article.content></span>
            </section>
            <section class="comment-list">
                <div class="comment" :key="cindex" v-for="(comment,cindex) in article.comment">
                    <a :title="comment.title">{{comment.title}}</a>&nbsp;
                    <span><a class="mention">{{comment.mention}}</a>{{comment.comment}}</span>
                </div>
            </section>
            <section class="times">
                <time :datetime="article.datetime" :title="article.dateTitle">{{article.dateAgo}}</time>
            </section>
            <section class="add-comment">
                <input data-name="commentInput" type="text" placeholder="Add a comment..." @keypress="addComment"/>
            </section>
        </div>
    </article>
</div>
</template>

<script>
    export default {
        name: 'Article',
        props: {
            menu: Array,
            articles: Array
        },
        methods:{
            btnLike(){
                const likeSvg = '<svg aria-label="Unlike" class="_8-yf5 " width="24" height="24" fill="#ed4956" viewBox="0 0 48 48"><path clip-rule="evenodd" d="M35.3 35.6c-9.2 8.2-9.8 8.9-11.3 8.9s-2.1-.7-11.3-8.9C6.5 30.1.5 25.6.5 17.8.5 9.9 6.4 3.5 13.7 3.5 20.8 3.5 24 8.8 24 8.8s3.2-5.3 10.3-5.3c7.3 0 13.2 6.4 13.2 14.3 0 7.8-6.1 12.3-12.2 17.8z" fill-rule="evenodd"></path></svg>';
                const unlikeSvg = '<svg aria-label="Like" fill="#262626" viewBox="0 0 48 48" width="24" height="24"><path clip-rule="evenodd" d="M34.3 3.5C27.2 3.5 24 8.8 24 8.8s-3.2-5.3-10.3-5.3C6.4 3.5.5 9.9.5 17.8s6.1 12.4 12.2 17.8c9.2 8.2 9.8 8.9 11.3 8.9s2.1-.7 11.3-8.9c6.2-5.5 12.2-10 12.2-17.8 0-7.9-5.9-14.3-13.2-14.3zm-1 29.8c-5.4 4.8-8.3 7.5-9.3 8.1-1-.7-4.6-3.9-9.3-8.1-5.5-4.9-11.2-9-11.2-15.6 0-6.2 4.6-11.3 10.2-11.3 4.1 0 6.3 2 7.9 4.2 3.6 5.1 1.2 5.1 4.8 0 1.6-2.2 3.8-4.2 7.9-4.2 5.6 0 10.2 5.1 10.2 11.3 0 6.7-5.7 10.8-11.2 15.6z" fill-rule="evenodd"></path></svg>';
                let articlebtn = event.target.closest('[data-name]');
                let articlebtnLabel = articlebtn.children[0].getAttribute('aria-label');
                let articleId = event.target.closest('[data-id]').getAttribute('data-id');
                let likeCount = document.querySelector(`[data-id="${articleId}"] [data-name="likesCount"]`);
                if (articlebtnLabel == 'Like'){
                    articlebtn.innerHTML = likeSvg;
                    likeCount.innerText = parseInt(likeCount.innerText) + 1;
                } else {
                    articlebtn.innerHTML = unlikeSvg;
                    likeCount.innerText = parseInt(likeCount.innerText) - 1;
                }
            },
            btnComment(){
                const articleId = event.target.closest('[data-id]').getAttribute('data-id');
                const inputText = document.querySelector(`[data-id="${articleId}"] [data-name="commentInput"]`);
                inputText.focus();
            },
            addComment(){
                const keyword = event;
                if (keyword.key =='Enter'){
                    const id = event.target.closest('[data-id]').getAttribute('data-id');
                    const index = event.target.closest('[data-id]').getAttribute('data-index');
                    let comment = document.querySelector(`[data-id="${id}"] [data-name="commentInput"]`).value;
                    const newComment = new Object();
                    newComment.title = "You";
                    newComment.mention = '';
                    newComment.comment = comment;
                    this.articles[index].comment.push(newComment);
                    document.querySelector(`[data-id="${id}"] [data-name="commentInput"]`).value = '';
                }
            },
            btnShare(){
                navigator.clipboard.writeText(document.URL);
                const msg = '已複製網址';
                this.$bus.$emit('toastmsg' ,msg);
            },
            showModal(){
                let index = event.target.closest('[data-id]').getAttribute('data-index');
                this.$bus.$emit('dataindex' , index);
            },
            hideArticle(hideIndex){
                this.articles.splice(hideIndex, 1);

            }
        },
        mounted(){
            this.$bus.$on('deleteIndex', (index)=>{
                this.hideArticle(index);
            });

            let busEvent = this.$bus;
            window.onscroll = function(){
                let canFetch = true;
                if (canFetch && window.innerHeight + window.scrollY >= document.body.scrollHeight){
                    let lastid = document.getElementsByClassName('card-list')[0].lastElementChild.dataset.id;
                    busEvent.$emit('lastId' , lastid);
                    busEvent.$on('fetch', (val)=>{
                        canFetch = val;
                    })
                }
            }
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    .card-list {
        max-width: 614px;
        margin: 0 auto;
    }
    .card-wrapper {
        margin-bottom: 32px;
        border: 1px solid var(--common-border-color);
        border-radius: 3px;
        background-color: var(--card-bg-color);
    }

    .card-wrapper .header {
        padding: 16px;
        height: 60px;
        box-sizing: border-box;
        display: flex;
        flex-direction: row;
        align-items: center;
    }

    .card-wrapper .header .avatar {
        height: 32px;
        width: 32px;
    }

    .card-wrapper .header .avatar img {
        border-radius: 50%;
    }

    .card-wrapper .header .desc {
        margin-left: 16px;
    }

    .card-wrapper .header .title {
        font-weight: bold;
    }

    .card-wrapper .header .options {
        margin-left: auto;
    }

    .card-wrapper .actions button {
        background: 0 0;
        border: 0;
        padding: 8px;
    }

    .card-wrapper .actions {
        margin-top: 4px;
        padding: 0 16px;
        display: flex;
        align-items: center;
    }

    .card-wrapper .actions button:first-child {
        margin-left: -8px;
    }

    .card-wrapper .actions button:last-child {
        margin-left: auto;
        margin-right: -8px;
    }

    .card-wrapper .bottom section {
        padding: 0 16px;
    }

    .card-wrapper .likes {
        margin: 8px 0;
    }

    .card-wrapper .likes .liked-by {
        width: 20px;
        height: 20px;
        margin-right: 4px;
        display: inline-block;
    }

    .card-wrapper .likes .liked-by img {
        border-radius: 50%;
    }

    .card-wrapper .bottom a {
        font-weight: bold;
    }

    .card-wrapper .bottom a.mention,
    .card-wrapper .bottom a.hashtag {
        color: var(--hashtag-text-color);
        font-weight: normal;
    }

    .card-wrapper .bottom .times {
        color: var(--times-text-color);
        margin: 4px 0;
        text-transform: uppercase;
    }

    .card-wrapper .bottom .add-comment {
        height: 56px;
        display: flex;
        align-items: center;
        border-top: 1px solid #eee;
    }

    .card-wrapper .bottom .add-comment input {
        border: 0;
        width: 100%;
    }
    .options{
        cursor: pointer;
    }


    .liked-by {
        width: 20px;
    }


</style>