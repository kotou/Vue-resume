<template>
    <div>
        <h2>{{title}}</h2>
        <div class="wrap" v-for="(item,index) in items">
            <el-form>
                <el-form-item v-for="key in keys" :label="labels[key]" :key="key">
                    <el-input v-model="item[key]"></el-input>
                </el-form-item>
            </el-form>
            <i class="el-icon-close" @click="removeItem(index)"></i>
        </div>
        <div style="position: relative;">
            <el-button type="primary" icon="el-icon-plus" @click="addItem" style="position: absolute;top:0;right:0;"></el-button>
        </div>
    </div>
</template>
<script>
    export default {
        props: ['items', 'labels','title'],
        computed: {
            keys() {
                return Object.keys(this.items[0])
            }
        },
        methods: {
            addItem() {
                const empty = {}
                this.keys.map((key) => {
                    empty[key] = ''
                }),
                    this.items.push(empty)
            },
            removeItem(index) {
                this.items.splice(index, 1)
            }
        }
    }
</script>