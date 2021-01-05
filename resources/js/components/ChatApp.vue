<template>
    <div class="chat-app">
        <conversation :contact ="selectedContact" :messages="messages"></conversation>
        <contact :contacts = "contacts" @selected="startConversationWith"></contact>
    </div>
</template>
<script>
    import Conversation from "./Conversation";
    import Contact from "./Contact";
    export default {
        components: {Conversation, Contact},
        props :{
          type : Object,
          required : true
        },
        data(){
            return {
                selectedContact : null,
                messages : [],
                contacts : [],
            }
        },
        mounted() {
            axios.get('/contacts')
                .then((response) =>{
                    // console.log(response.data)
                    this.contacts = response.data
            });
        },
        methods:{
            startConversationWith(contact){
                axios.get(`/conversation/${contact.id}`)
                .then((response)=>{
                    console.log(response.data)
                    this.messages = response.data;
                    this.selectedContact = contact
                })
            }
        }
    }
</script>

<style scoped lang="scss">
.chat-app{
    display: flex;
}
</style>
