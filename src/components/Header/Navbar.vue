 <template>
  <div>
    <nav class="navbar">
      <div style="display: flex;">
        <h3 @click="goHome" class="nav-logo">OLCHA</h3>
        <div class="nav-but">0% {{ $t('navbar.index') }}</div>
        <div class="nav-but-two">{{ $t('navbar.price') }}</div>
        <div class="nav-but">{{ $t('navbar.news') }}</div>
      </div>
      <div style="display: flex; align-items: center;">
<button @click="goToProducts" class="nav-button">
      <div>
        <span class="ham"></span>
        <span class="ham"></span>
        <span class="ham"></span>
      </div>
      {{ $t('navbar.collaboration') }}</button>
      <div class="lang">RU<label class="switch">
  <input v-model="swi" @click="change" type="checkbox">
  <span class="slider"></span>
</label>EN</div>
      </div>
    </nav>
    <div style="display: flex; justify-content: flex-end">
      <el-badge :value="liked_products?.length" class="item">
        <el-button class="button-like" @click="goToFavourites">
          <div>
            <img
              class="button-like-img"
              src="https://cdn-icons-png.flaticon.com/512/1077/1077035.png"
              alt=""
            />
            {{ $t('navbar.favourite') }}
          </div>
        </el-button>
      </el-badge>
      <el-badge :value="products_in_cart?.length" class="item">
        <el-button @click="goToCart" class="button-like">
          <div>
            <img
              class="button-like-img"
              src="https://upload.wikimedia.org/wikipedia/commons/thumb/b/b4/%D0%98%D0%BA%D0%BE%D0%BD%D0%BA%D0%B0_%D0%BF%D1%80%D0%BE%D0%B4%D1%83%D0%BA%D1%82%D0%BE%D0%B2%D0%BE%D0%B9_%D0%BA%D0%BE%D1%80%D0%B7%D0%B8%D0%BD%D1%8B_%28ei%29.svg/1200px-%D0%98%D0%BA%D0%BE%D0%BD%D0%BA%D0%B0_%D0%BF%D1%80%D0%BE%D0%B4%D1%83%D0%BA%D1%82%D0%BE%D0%B2%D0%BE%D0%B9_%D0%BA%D0%BE%D1%80%D0%B7%D0%B8%D0%BD%D1%8B_%28ei%29.svg.png"
              alt=""
            />
            {{ $t('navbar.cart') }}
          </div>
        </el-button>
      </el-badge>
    </div>
  </div>
</template>
  
<script>
import { ElPageHeader, ElButton } from "element-plus";
import { mapGetters } from "vuex";
import {i18n} from '../../main'
export default {
  name: "Navbar",
  data() {
    return {
      cartLength: 0,
      swi:false
    };
  },
  methods: {
    change(){
      if(this.swi== true){
        this.$i18n.locale='ru'
      }else{
        this.$i18n.locale='en'
      }
    },
    goToPage(link) {
      this.$router.push(link.path);
    },
    goToProducts(){
      this.$router.push("/products");
    },
    goToFavourites() {
      this.$router.push("/favourites");
    },
    goHome(){
      this.$router.push("/");
    },
    goToCart() {
      this.$router.push("/cart");
    },
  },
  computed: {
    ...mapGetters(["nav_links", "liked_products", "products_in_cart"]),
  },
  mounted() {},
};
</script>
<style scoped>
*,
*:before,
*:after {
  padding: 0;
  margin: 0;
  border: 0;
}
.lang{
 display: flex;
 justify-content: center;

}

/* The switch - the box around the slider */
.switch {
 font-size: 17px;
 position: relative;
 display: inline-block;
 width: 45px;
 height: 20px;
}

/* Hide default HTML checkbox */
.switch input {
 opacity: 1;
 width: 0;
 height: 0;
}

/* The slider */
.slider {
 position: absolute;
 cursor: pointer;
 top: 0;
 left: 0;
 right: 0;
 bottom: 0px;
 background: #fff;
 transition: .4s;
 border-radius: 30px;
 border: 1px solid #ccc;
}

.slider:before {
 position: absolute;
 content: "";
 height: 1em;
 width: 1em;
 border-radius: 16px;
 top: 0;
 bottom: 0;
 background-color: white;
 box-shadow: 0 2px 5px #999999;
 transition: .4s;
}

input:checked + .slider {
 background-color: #ca80c0;
 border: 1px solid transparent;
}

input:checked + .slider:before {
 transform: translateX(1.5em);
}

.navbar {
  display: flex;
  background-repeat: no-repeat;
  align-items: center;
  width: 100%;
  background: #da002b;
  height: 70px;
  justify-content: space-between;
}
.el-page-header__back {
  display: none !important;
}
.el-page-header__header .el-divider {
  display: none !important;
}
.nav-logo {
  font-size: 30px;
  color: white;
  margin-left: 20px;
  cursor: pointer;
  transition: 0.5s;
}
.nav-logo:hover{
color: black;
}
.nav-but {
  color: #da002b;
  background: white;
  font-size: 18px;
  font-weight: 700;
  padding: 10px;
  border-radius: 8px;
  margin-left: 15px;
}
.nav-but-two {
  color: white;
  background: #da002b;
  font-size: 18px;
  font-weight: 700;
  padding: 8px;
  border-radius: 8px;
  border: 2px solid white;
  margin-left: 15px;
}
.nav-button{
  padding: 8px;
  font-size: 18px;
  font-weight: 700;
  border-radius: 8px;
  border: 2px solid white;
  background: transparent;
  color: white;
  display: flex;
  align-items: center;
  cursor: pointer;
  transition: 0.5s;
  margin-right: 50px;
}
.nav-button:hover{
  border: 2px solid black;
  color: black;
}
.nav-button:hover .ham{
  background: black;
}
.ham{
  display: block;
    width: 20px;
    height: 2px;
    background: white;
    margin-bottom: 3px;
    margin-right: 8px;
    transition: 0.5s;
}
</style>
