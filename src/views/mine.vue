<template>
  <div>
    <div class="qwer">
      <div class="me" v-if="flag">
        <div class="headInfo">
          <div class="loginYu" @click="$router.push('/logOut')">
            <img v-if="imageUrl" :src="imageUrl" class="avatar" />
          </div>
          <div class="head-profile">
            <p class="user-id" v-if="userInfo">{{userInfo._id}}</p>
            <p v-else class="user-id" @click="handlelogin">登录/注册</p>
            <p class="user-phone">
              <i class="fa fa-mobile"></i>
              <span v-if="userInfo">{{encryPhone(userInfo.phone)}}</span>
              <span v-else>登录后享受更多特权</span>
            </p>
          </div>
          <i class="fa fa-angle-right"></i>
        </div>
      </div>
      <div v-else>
        <mt-nav></mt-nav>
      </div>
      <elm-header v-if="flag"></elm-header>
      <mtmain v-else></mtmain>
      <elm-main></elm-main>
    </div>
  </div>
</template>

<script>
//elm
import elmHeader from "../components/mine-lem/elmHeader";
import elmMain from "../components/mine-lem/elmMain";
//mt
import mtNav from "../components/mine-mt/mtNav";
import mtmain from "../components/mine-mt/mtmain";
import { mapActions, mapGetters, mapMutations, mapState } from "vuex";
export default {
  name: "mine",
  components: {
    elmHeader,
    elmMain,
    mtNav,
    mtmain
  },
  computed: {
    ...mapState(["flag"])
  },
  data() {
    return {
      userInfo: "",
      imageUrl: ""
    };
  },
  beforeRouteEnter(to, from, next) {
    next(vm => vm.getData());
  },
  created() {
    //从localStorage中取出照片
    this.imageUrl = localStorage.getItem("img");
  },
  methods: {
    handlelogin() {
      this.$router.push("/phoneLogin");
    },

    getData() {
      const user_id = localStorage.ele_login;
      //   console.log(user_id);
      this.$axios(`/api/user/user_info/${user_id}`).then(res => {
        // console.log(res.data);
        this.userInfo = res.data;
      });
    },
    encryPhone(phone) {
      return phone.replace(/(\d{3})\d{4}(\d{4})/, "$1****$2");
    }
  }
};
</script>

<style scoped>
.qwer {
  background-color: #ffc501;
}
.me {
  width: 100%;
  height: 100%;
  overflow: auto;
  box-sizing: border-box;
}
.headInfo {
  display: flex;
  background-image: linear-gradient(90deg, #0af, #0085ff);
  padding: 6.666667vw 4vw;
  color: #fff;
  align-items: center;
}
.loginYu {
  margin-right: 6px;
  width: 60px;
  height: 60px;
  border-radius: 50%;
  background-size: 100%;
  background-color: #f3f6fc;
}
.avatar {
  width: 60px;
  height: 60px;
  border-radius: 50%;
  background-position: 0px 0px;
  background-size: 60px;
  background-image: url(https://shadow.elemecdn.com/faas/h5/static/sprite.3ffb5d8.png);
}
.head-profile {
  overflow: hidden;
  margin-left: 4.8vw;
  flex-grow: 1;
}
.head-profile .user-id {
  max-width: 40vw;
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
  font-size: 1.3rem;
  margin-bottom: 2.133333vw;
  font-weight: 700;
  display: flex;
  align-items: center;
}
.head-profile .user-phone {
  display: flex;
  align-items: center;
  font-size: 0.8rem;
}
.user-phone > i {
  margin-right: 0.666667vw;
  font-size: 1rem;
}
.headInfo > i {
  font-size: 1.2rem;
}
</style>