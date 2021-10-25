<template>
<div ref="el">
    <nodeHeader  title="Script"/>
    <p>Open in navbar</p>
    <el-button type="info"  size="small" @click="drawer = true">Edit</el-button>
    <teleport to="body">
        <el-drawer
        v-model="drawer"
        title="Edit Optinos"
        :direction="direction"
        :before-close="handleClose"

        >
            <p>Autosave</p>
            <el-input
            v-model="textarea"
            :rows="8"
            df-script
             @change="updateSelect" 
            type="textarea"
            placeholder="Please input"
        />
        </el-drawer>
    </teleport>

</div>
</template>

<script>
import { defineComponent, ref, getCurrentInstance, nextTick, onMounted } from 'vue'
import nodeHeader from './nodeHeader.vue'
import { ElMessageBox } from 'element-plus'


export default defineComponent({
    components: {
        nodeHeader
    },
    setup() {
        const el = ref(null);
        const textarea = ref('');
        let df = null
        const nodeId = ref(0);
        const dataNode = ref({});
        const drawer = ref(false);
        const direction = ref('rtl');
        const handleClose = (done) => {
            ElMessageBox.confirm('Are you sure you want to close this?')
                .then(() => {
                done()
                })
                .catch(() => {
                // catch error
                })
        }
     df = getCurrentInstance().appContext.config.globalProperties.$df.value;
    
     const updateSelect = (value) => {
            dataNode.value.data.script = value;
            df.updateNodeDataFromId(nodeId.value, dataNode.value);
        }

     onMounted(async () => {
            await nextTick()
            nodeId.value = el.value.parentElement.parentElement.id.slice(5)
            dataNode.value = df.getNodeFromId(nodeId.value)
            textarea.value = dataNode.value.data.script;
        });

    return {
      el,
      drawer,
      direction,
      handleClose,
      textarea,
      updateSelect
    }
    },
    
   
})
</script>
<style scoped>
p {
    margin: 5px;
    margin-bottom: 10px;
}
</style>
