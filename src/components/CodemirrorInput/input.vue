<template>
    <div class="el-cm-input" ref="cmInput"></div>
</template>

<script>
import { EditorView } from "codemirror"
import { EditorState } from "@codemirror/state"
export default {
    name: "cm-input",
    mounted() {
        new EditorView({
            extensions: [
                EditorState.transactionFilter.of(tr => {
                    return tr.newDoc.lines > 1 ? [] : [tr]
                })],
            parent: this.$refs.cmInput
        })
    }
}
</script>