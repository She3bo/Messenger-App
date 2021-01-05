<template>
    <div class="conversations">
        <h1>{{contact ? contact.name : "Select a Contact"}}</h1>
        <MessagesFeed :contact="contact" :messages="messages"></MessagesFeed>
        <MessageComposer @send="sendMessage"></MessageComposer>
    </div>
</template>

<script>
    import MessagesFeed from "./MessagesFeed";
    import MessageComposer from "./MessageComposer";
    export default {
        name: "Conversation",
        components: {MessageComposer, MessagesFeed},
        props:{
            contact: {
                 type: Object,
                 default: null
            },
            messages: {
                type: Array,
                default: []
            },
        },
        methods:{
            sendMessage(text){
                 console.log(text)
            },
        },
    }
</script>

<style scoped lang="scss">
.conversations{
    flex: 5;
    display: flex;
    max-height: 100%;
    flex-direction: column;
    justify-content: space-between;
    h1 {
        font-size: 20px;
        padding: 10px;
        margin: 0;
        border-bottom: 1px dashed lightgray;
    }

}
</style>
