<template>
    <div class="modal" id="modal" data-name="modal" data-index="">
        <div class="modal-content">
          <button class="item danger" data-name="delete">Hide</button>
          <button class="item" data-name="cancel">Cancel</button>
        </div>
    </div>
</template>

<script>
export default {
  name: 'Modal',
  created(){
    this.$bus.$on('dataindex' , (dataindex)=>{
        document.getElementById('modal').setAttribute('data-index' , dataindex);
        // show modal
        document.getElementById('modal').style.display = 'flex';
        // can not move
        document.body.style.overflow = 'hidden';
        // set event handler
        document.getElementById('modal').addEventListener('click', this.clickEvent);
    })
  },
  methods:{
      clickEvent(){
          const data = event.target;
          const dataType = data.dataset.name;
          const index = data.closest('[data-name="modal"]').dataset.index;
                
          switch(dataType){
              case 'delete':
                this.$bus.$emit('deleteIndex', index);
                document.getElementById('modal').style.display = 'none';
                document.body.style.overflow = '';
                break;
              case 'cancel':
              case 'modal':
                document.getElementById('modal').style.display = 'none';
                document.body.style.overflow = '';
                break;
          }
      }
  }   
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    .modal {
        background-color: rgba(0, 0, 0, .65);
        position: fixed;
        left: 0;
        top: 0;
        right: 0;
        bottom: 0;
        z-index: 1;
        justify-content: center;
        align-items: center;
        display: none;
        /*display: flex; */
    }

    .modal .modal-content {
        width: 400px;
        background-color: #fff;
        border-radius: 12px;
        overflow: hidden;
    }

    .modal .modal-content .item {
        display: block;
        width: 100%;
        height: 48px;
        border: 0;
        padding: 0;
        box-sizing: border-box;
    }

    .modal .modal-content .item.danger {
        color: rgba(237, 73, 86, 1);
        font-weight: 700;
    }

    .modal .modal-content .item:not(:first-child) {
        border-top: 1px solid rgb(219, 219, 219);
    }
</style>
