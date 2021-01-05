<template>
    <div class="composer">
        <textarea v-model="message" @keydown.enter="send" placeholder="  Message..."></textarea>
    </div>
</template>

<script>
export default {
    name: "MessageComposer",
    data(){
      return{
       message:""
      }
    },
    methods:{
        send(){
              if(this.message === "")
                  return ;
              this.$emit('send',this.message);
              this.message=""
        }
    }
}
</script>

<style lang="scss" scoped>
.composer{
    textarea{
        resize: none;
        width: 85%;
        border-radius: 25px;
        height: 35px;
        &:focus{
            outline: none;
        }
    }
}

</style>
