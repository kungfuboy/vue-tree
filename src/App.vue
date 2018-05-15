<template>
    <div id="app">
        <vue-tree status="true" :data="data"></vue-tree>
        <!-- <button @click="show">oo</button> -->
    </div>
</template>

<script>
import vueTree from './components/vue-tree'

export default {
    name: 'App',
    data() {
        return {
            data: [{
                label: 'root',
                children: [
                    {
                        label: '一级 1',
                        children: [{
                            label: '二级 1-1',
                            children: [{
                                label: '三级 1-1-1'
                            }]
                        }]
                    }, {
                        label: '一级 2',
                        children: [{
                            label: '二级 2-1',
                            children: [{
                                label: '三级 2-1-1'
                            }]
                        }, {
                            label: '二级 2-2',
                            children: [{
                                label: '三级 2-2-1'
                            }]
                        }]
                    }, {
                        label: '一级 3',
                        children: [{
                            label: '二级 3-1',
                            children: [{
                                label: '三级 3-1-1'
                            }]
                        }, {
                            label: '二级 3-2',
                            children: [{
                                label: '三级 3-2-1',
                                children: [{
                                    label: '二级 3-1',
                                    children: [{
                                        label: '三级 3-1-1'
                                    }]
                                }]
                            }]
                        }]
                    }
                ]
            }]
        }
    },
    methods: {
        show() {
            console.log(this.data)
        }
    },
    components: {
        vueTree
    }
}
</script>

<style>

</style>
