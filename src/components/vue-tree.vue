<template>
   <ul v-show="!!data && !!data.length">
       <li v-for="(item, index) in data" :key="index">
           <i @click="addChild(item.children)">add</i>
           <span @click="active = index" v-if="index !== active">{{item.label}}</span>
           <input @keyup="handleEnter($event, item.label, index)" type="text" :value='item.label' v-else />
           <vue-tree :data='item.children'></vue-tree>
       </li>
   </ul>
</template>
<script>
export default {
    name: 'vueTree',
    props: ['data'],
    data() {
        return {
            active: ''
        }
    },
    methods: {
        handleEnter(e, value, i) {
            if(e.keyCode === 13) {
                this.data[i].label = e.target.value
                this.active = ''
            }
        },
        addChild(data) {
            data = data || []
            data.push({
                label: 'new'
            })
        }
    }
}
</script>
<style lang="less">
li {
    position: relative;
    width: 220px;
    i {
        position: absolute;
        cursor: pointer;
        right: 0;
        top: 0;
    }
}
</style>

