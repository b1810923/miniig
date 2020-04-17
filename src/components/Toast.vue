<template>
    <div class="toast hide" id="toast"></div>
</template>

<script>
export default {
  name: 'Toast',
  props: {
    msg:String
  },
  created(){
    let timeout;
    this.$bus.$on('toastmsg', (msg)=>{
        document.getElementById('toast').innerText = msg;
        document.getElementById('toast').classList = 'toast';
        
        if(timeout){
            clearTimeout(timeout);
        }
        timeout = setTimeout(function(){
            document.getElementById('toast').classList = "toast hide";
        }, 1000);
    });
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.toast {
    position: fixed;
    bottom: 0;
    width: 100%;
    padding: 12px;
    line-height: 18px;
    display: flex;
    align-items: center;
    font-size: 14px;
    color: #fff;
    background-color: #262626;
    opacity: 0.8;
    transition: transform 0.3s;
}

.toast.hide {
    transform: translateY(42px);
}
</style>
