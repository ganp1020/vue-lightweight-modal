<template>
    <div id="app">
        <img alt="Vue logo" src="./assets/logo.png">
        <Dialog title="弹窗标题" :visible.sync="visible">
            <h1>这是dialog的body</h1>
            <h2 slot="footer">这是dialog的footer</h2>
        </Dialog>
        <button @click="openDialog">点击显示弹窗</button>
    </div>
</template>

<script>
    import Dialog from './components/Dialog.vue'

    export default {
        name: 'app',
        components: {
            Dialog
        },
        data() {
            return {
                visible: false
            }
        },
        methods: {
            openDialog() {
                this.visible = true // 通过data显式控制dialog
            }
        }
    }
</script>

<style lang="scss">
    #app {
        font-family: 'Avenir', Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
        margin-top: 60px;
    }
</style>
