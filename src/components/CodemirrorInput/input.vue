<template>
    <div class="el-cm-input" ref="cmInput"></div>
</template>

<script>
import { EditorView } from "codemirror"
import { EditorState } from "@codemirror/state"
import { ViewPlugin } from "@codemirror/view"
export default {
    name: "cm-input",
    mounted() {
        const editorView = new EditorView({
            doc: "test",
            extensions: [
                ViewPlugin.fromClass(class {
                    update(update) {
                        if (update.docChanged) {
                            console.log("new Value: {}", update.state.doc.toString());
                        } else {
                            console.log(update)
                        }
                    }
                }),
                EditorState.transactionFilter.of(tr => {
                    return tr.newDoc.lines > 1 ? [] : [tr]
                })],
            parent: this.$refs.cmInput
        });
        window.xx = editorView;
        setTimeout(() => {
            editorView.dispatch({
                changes: {
                    from: editorView.state.selection.ranges[0].from,
                    to: editorView.state.selection.ranges[0].to,
                    insert: "测试"
                }
            })
        }, 3000);
    }

}
</script>