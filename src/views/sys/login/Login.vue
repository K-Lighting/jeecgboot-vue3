<template>
  <div id="userLayout" :class="['user-layout-wrapper', device]">
    <div class="container1">
      <LoginForm />
    </div>
  </div>
</template>
<script lang="ts" setup>
  import { computed } from 'vue';
  import { AppLogo } from '/@/components/Application';
  import { AppLocalePicker, AppDarkModeToggle } from '/@/components/Application';
  import LoginForm from './LoginForm.vue';
  import ForgetPasswordForm from './ForgetPasswordForm.vue';
  import RegisterForm from './RegisterForm.vue';
  import MobileForm from './MobileForm.vue';
  import QrCodeForm from './QrCodeForm.vue';
  import { useGlobSetting } from '/@/hooks/setting';
  import { useI18n } from '/@/hooks/web/useI18n';
  import { useDesign } from '/@/hooks/web/useDesign';
  import { useLocaleStore } from '/@/store/modules/locale';
  import { useLoginState, LoginStateEnum } from './useLogin';
  defineProps({
    sessionTimeout: {
      type: Boolean,
    },
  });

  const globSetting = useGlobSetting();
  const { prefixCls } = useDesign('login');
  const { t } = useI18n();
  const localeStore = useLocaleStore();
  const showLocale = localeStore.getShowPicker;
  const title = computed(() => globSetting?.title ?? '');
  const { handleBackLogin } = useLoginState();
  handleBackLogin();
</script>
<style lang="less" scoped>
  #userLayout.user-layout-wrapper {
    height: 100%;
    width: 100%;
    background: #f0f2f5 url(../../../assets/images/loginbackground_update.png);
    background-position: center 0;
    background-repeat: no-repeat;
    background-attachment: fixed;
    background-size: cover;
    -webkit-background-size: cover; /* 兼容Webkit内核浏览器如Chrome和Safari */
    -o-background-size: cover; /* 兼容Opera */
    display: flex;
    &.mobile {
      .container {
        .main {
          max-width: 368px;
          width: 98%;
        }
      }
    }
    .title-box {
      height: 80px;
      display: flex;
      align-items: center;
      margin-left: 10%;
      margin-top: 6%;
      img {
        height: 48px;
        width: 48px;
      }
    }
    .container1 {
      padding: 40px;
      border-radius: 20px;
      margin: auto;
      // margin-right: 15%;
      background: #fff;
      // background-color: #eaeaea1c;
      // opacity: 1;
      // background-size: 100%;
      // padding: 110px 0 144px;
      position: relative;
  
      a {
        text-decoration: none;
      }
      }
    }
  </style>