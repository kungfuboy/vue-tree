<template>
    <ul v-show="!!data && !!data.length">
        <li v-for="(item, index) in data" :key="index">
            <i class='list' @click="handleList"></i>
            <i class='add' @click="addChild(item)">add</i>
            <i class='del' @click="deleteChild(index)">del</i>
            <span @click="active = index" v-if="index !== active">{{item.label}}</span>
            <input @keyup="handleEnter($event, index)" type="text" :value='item.label' v-else />
            <vue-tree v-if="status" :data='item.children'></vue-tree>
        </li>
    </ul>
</template>
<script>
export default {
    name: 'vueTree',
    props: ['data'],
    data() {
        return {
            active: '',
            status: false
        }
    },
    methods: {
        handleEnter(e, i) {
            if (e.keyCode === 13) {
                this.data[i].label = e.target.value
                this.active = ''
            }
        },
        addChild(data) {
            const newChild = { label: 'new...', children: [] }
            if (!data.children) {
                this.$set(data, 'children', [])
            }
            data.children.push(newChild)
        },
        deleteChild(index) {
            this.data.splice(index, 1)
        },
        handleList() {
            this.status = !this.status
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
    top: 0;
    &.add {
      right: 30px;
    }
    &.del {
      right: 0;
    }
  }
}
</style>

