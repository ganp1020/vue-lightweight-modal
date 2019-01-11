<template>
    <div class="dialog-container">
        <div class="dialog__wrapper" v-if="visible" @click="closeModal">
            <div class="dialog">
                <div class="dialog__header">
                    <div class="dialog__title">{{ title }}</div>
                </div>
                <div class="dialog__body">
                    <slot></slot>
                </div>
                <div class="dialog__footer">
                    <slot name="footer"></slot>
                </div>
            </div>
        </div>
        <div class="modal" v-show="visible"></div>
    </div>
</template>

<script>
    export default {
        props: {
            title: String,
            visible: {
                type: Boolean,
                default: false
            }
        },
        methods: {
            close() {
                this.$emit('update:visible', false) // 传递关闭事件
            },
            closeModal(e) {
                if (this.visible) {
                    document.querySelector('.dialog').contains(e.target) ? '' : this.close(); // 判断点击的落点在不在dialog对话框内，如果在对话框外就调用this.close()方法关闭对话框
                }
            }
        }
    }
</script>
<style lang="scss" scoped>
    .dialog__wrapper{
        z-index: 2001;
        position: fixed;
        top: 0;
        right: 0;
        bottom: 0;
        left: 0;
        overflow: auto;
        margin: 0;
        .dialog{
            position: relative;
            margin: 0 auto 50px;
            background: #fff;
            border-radius: 2px;
            box-shadow: 0 1px 3px rgba(0,0,0,.3);
            box-sizing: border-box;
            width: 50%;
        }
    }
    .modal{
        z-index: 2000;
        position: fixed;
        left: 0;
        top: 0;
        width: 100%;
        height: 100%;
        opacity: .5;
        background: #000;
    }
</style>