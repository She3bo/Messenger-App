<template>
    <div class="feed">
        <ul v-if="contact">
            <li v-for="message in messages" :key="message.id" :class="`message ${message.to === contact.id ? ' sent' : ' received'}`">
                <div class="text">
                    {{message.text}}
                </div>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    name: "MessagesFeed",
    props:{
        messages:{
            type:Array,
            required : true,
        },
        contact:{
            type: Object,
        },
    }
}
</script>

<style scoped lang="scss">
.feed{
    background: #f0f0f0;
    height: 100%;
    max-height: 380px;
    overflow: scroll;
    ul{
        list-style: none;
        padding: 5px;
        li {
            &.message {
                margin: 10px 0;
                width: 100%;

                .text {
                    max-width: 200px;
                    border-radius: 5px;
                    padding: 12px;
                    display: inline-block;
                }

                &.received {
                    text-align: right;

                    .text {
                        background: #b2b2b2;
                    }
                }

                &.sent {
                    text-align: left;

                    .text {
                        background: #81c4f9;
                    }
                }
            }
        }
    }
}

</style>
