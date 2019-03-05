<template>
  <div class="wrapper">
    <text class="greeting">The environment is ready!</text>
    <mpbp-button text="打开dialog试一试" @mpbpBtnClicked="onClick"></mpbp-button>
  </div>
</template>

<script>
import { mpbpButton, mpbpDialog } from '@mpbp/mpbp-ui'

const modal = weex.requireModule('modal')

export default {
  name: 'App',
  components: {
    mpbpButton,
  },
  methods: {
    onClick() {
      mpbpDialog(
        {
          title: '开店宝',
          content: '通知可能包含提醒，声音和图标',
          actions: [
            {
              text: '取消',
              highlight: false
            },
            {
              text: '同意',
              highlight: true
            }
          ],
          callback(index) {
            modal.toast({
              message: index
            })
          }
        }
      )
    }
  }
}
</script>

<style scoped>
  .wrapper {
    justify-content: center;
    align-items: center;
  }
  .logo {
    width: 424px;
    height: 200px;
  }
  .greeting {
    text-align: center;
    margin-top: 70px;
    font-size: 50px;
    color: #41B883;
  }
  .message {
    margin: 30px;
    font-size: 32px;
    color: #727272;
  }
</style>