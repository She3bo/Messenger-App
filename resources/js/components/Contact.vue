<template>
    <div class="contact-list">
        <ul>
            <li v-for="(contact,index) in contacts" :key="contact.id"  @click="selectContact(index,contact)" :class="{ 'selected': contact === selected }">
                 <div class="avatar">
                     <img :src="contact.image" :alt="contact.name">
                 </div>
                 <div class="contact">
                     <p class="name">{{contact.name}}</p>
                 </div>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    name: "Contact",
    data(){
        return{
            selected: 0,
        }
    },
    props:{
        contacts : {
            type : Array,
            default : [],
        },
    },
    methods:{
        selectContact(index,contact){
            this.selected = index;
            this.$emit('selected', contact);
        }
    }
}
</script>

<style scoped lang="scss">
.contact-list{
    flex:2;
    overflow: scroll;
    max-height: 100%;
    height: 470px;
    border-left-style: outset;
    ul{
        list-style: none;
        padding-left: 0;
        li{
            display: flex;
            position: relative;
            padding: 2px;
            border-bottom: 1px solid #aaaaaa;
            cursor: pointer;
            &.selected {
                background: #dfdfdf;
            }
            .avatar{
                display: flex;
                flex: 1;
                align-items: center;
                img{
                    width: 40px;
                    border-radius: 50%;
                    margin: 0 auto;
                }
            }
            .contact{
                flex: 3;
                overflow: hidden;
                display: flex;
                flex-direction: column;
                justify-content: center;
                font-size: 12px;
                p{
                    margin: 0;

                    &.name{
                        font-weight: bold;
                    }
                }
            }
        }
    }
}
</style>
