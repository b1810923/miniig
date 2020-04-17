<template>
<header>
    <a class="icon" v-for="(menus, index) in menu" :key="index">
        <span class="tooltip">{{menus.title}}</span>
        <div class="svg" v-html="menus.svg"></div>
    </a>
</header>
</template>

<script>
export default {
  name: 'Menu',
  props: {
    menu: Array
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
header{
    height: 3.437rem;
    background-color:var(--header-bg-color);
    border-bottom: 1px solid var(--header-border-color);
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    position: fixed;
    top: 0;
    width: 100%;
    opacity: 0.9;
}    
.icon{
    margin:0 16px;
    cursor: pointer;
}
.tooltip{
    text-align: center;
    position: absolute;
    font-size: 12px;
    top: calc(3.437rem - var(--tooltip-top-move));
    margin-left: calc(var(--tooltip-move) * (-1));
    width: 36px;
    padding: 4px;
    border-radius: 4px;
    color: white;
    background-color: var(--tooltip-bg-color);
    opacity: 6;
    display:none;
}
header svg:hover path{
    fill: var(--tooltip-hover-color);
}
.icon:hover .tooltip{
    display: block;
}
.svg{
    display: inline-block;
}
</style>
