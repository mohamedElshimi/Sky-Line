<template>
    <header class="w-full flex flex-wrap relative">
        <div class="min-h-[60px] w-full bg-gray-200" v-if="windowWidth >= 1023.999999999999999">
            <div class="w-10/12 mx-auto flex flex-wrap justify-between items-center h-full pt-3">
                <div class="flex items-center">
                    <i class="fa-solid fa-calendar text-primary"></i>
                    <p class="me-7 ms-5 text-sm">سبت , 23 ديسمبر , 2023</p>
                    <p class="text-primary">الاخبار السياحية</p>
                </div>
                <marquee direction="right" class="w-6/12 overflow-hidden whitespace-nowrap md:my-0 my-3">
                        المطاعم الحلال في جورجيا : أفضل 10 مطاعم حلال فى جورجيا لعام 2022 
                        - طقس جورجيا .. لتختار أفضل الأوقات لزيارتها 
                        - هل جورجيا تحتاج فيزا؟ … تأشيرة جورجيا للعرب 
                        - السفر من السعودية إلى جورجيا - كل ما يجب ان تعرفه 
                        - 10 نصائح هامة قبل السفر الى جورجيا
                        - ارقام الطوارئ في جورجيا – ستحتاجها عند المجئ للسياحة 
                        - السياحة العلاجية في جورجيا-أشهر الاماكن والمنتجعات
                        - 10 اماكن سياحية في جورجيا.. لم يزورها المسافرون العرب بعد
                        - السياحة في تبليسي وأهم 18 مكان يستحق زيارتك 
                        - السياحة في باتومي وأهم 14 مكان يستحق زيارتك 
                </marquee>
                <div class="flex items-center lg:mb-0 mb-3">
                    <div class="flex items-center bg-white px-2 py-1 rounded-3xl">
                        <i class="fa-solid fa-sun text-primary"></i>
                        <p class="mx-1 text-sm">7.84 C</p>
                        <p class="text-sm">Tbilis</p>
                    </div>
                    <button class="bg-primary text-white px-2 p-1 rounded-3xl flex items-center ms-3">
                        <i class="fa-solid fa-user text-sm"></i>
                        <p class="text-sm ms-2">دخول / تسجيل</p>
                    </button>
                </div>
            </div>
        </div>
        <div class="h-[250px] w-full overflow-hidden relative">
            <img src="../assets/Images/W8A7cfSFFqkctjTCafzWsZHM0Dd1Zz-meta2LPZg9in2Ykg2YTYp9mK2YYuanBn-.jpg" alt="Home Banner" class="absolute top-1/2 -translate-y-1/2 lg:h-auto h-full">
        </div>
        <div class="h-[70px] w-full shadow-md lg:order-none order-first">
            <div class="lg:w-10/12 md:w-11/12 px-7 mx-auto flex items-center h-full justify-between">
                <div class="h-full me-5 mx-auto py-2">
                    <img src="../assets/Images/sky-logo.png" class="h-full" alt="">
                </div>
                <nav class="me-auto lg:w-11/12 w-2/12 order-first h-full flex items-center">
                    <button class="resposive-icon px-3 py-2 text-black bg-secondry-1 hidden text-2xl" @click="toggleMenuBar" v-if="!menubarOpen"><i class="fa-solid fa-bars"></i></button>
                <button class="resposive-icon px-3 py-2 text-black bg-secondry-1 hidden text-2xl" @click="toggleMenuBar" v-if="menubarOpen"><i class="fa-solid fa-x"></i></button>
                    <ul class="flex flex-wrap items-center ul-menu h-full" v-if="menubarOpen || windowWidth >= 1023.999999999999999">
                        <li class="list-item">
                            <span class="span-dec relative w-full" :class="{ active: isRouteActive('/') }"><i class="fa-solid fa-house me-2"></i>الرئيسية</span>
                        </li>
                        <li class="list-item" @click="toggleSubMenu('1')">
                            <span class="span-dec relative"><i class="fa-solid fa-globe me-2"></i>رحلات سياحية<i class="fa-solid fa-caret-down text-primary ms-1" :class="iconRotate1"></i></span>
                            <ul class="sub-menu md:mt-0 mt-5" v-if="subMenu1">
                            <li :class="{ active: isRouteActive('/honordoctor') }" @click="toggleMenuBar"> <i class="fa-solid fa-map me-3"></i>رحلات سياحية لجورجيا</li>
                            <li :class="{ active: isRouteActive('/ProfessionalDoctorate') }" @click="toggleMenuBar"><i class="fa-solid fa-map me-3"></i>رحلات سياحية لأذربيجان</li>
                            </ul>
                        </li>
                        <li class="list-item" @click="toggleSubMenu('2')">
                            <span class="span-dec relative"><i class="fa-solid fa-info me-2"></i>عن الشركة<i class="fa-solid fa-caret-down text-primary ms-1" :class="iconRotate2"></i></span>
                            <ul class="sub-menu md:mt-0 mt-5" v-if="subMenu2">
                            <li :class="{ active: isRouteActive('/honordoctor') }" @click="toggleMenuBar"> <i class="fa-solid fa-circle-info me-3"></i> من نحن</li>
                            <li :class="{ active: isRouteActive('/ProfessionalDoctorate') }" @click="toggleMenuBar"><i class="fa-solid fa-phone me-3"></i> تواصل معنا</li>
                            <li :class="{ active: isRouteActive('/ProfessionalDoctorate') }" @click="toggleMenuBar"><i class="fa-solid fa-sheet-plastic me-3"></i> سياسة الشركة</li>
                            </ul>
                        </li>
                        <li class="list-item" @click="toggleSubMenu('3')">
                            <span class="span-dec relative"><i class="fa-solid fa-location-dot me-2"></i>فروعنا<i class="fa-solid fa-caret-down text-primary ms-1" :class="iconRotate3"></i></span>
                            <ul class="sub-menu md:mt-0 mt-5" v-if="subMenu3">
                            <li :class="{ active: isRouteActive('/honordoctor') }" @click="toggleMenuBar"> <i class="fa-solid fa-map me-3"></i> أذربيجان</li>
                            <li :class="{ active: isRouteActive('/ProfessionalDoctorate') }" @click="toggleMenuBar"><i class="fa-solid fa-map me-3"></i>جورجيا</li>
                            <li :class="{ active: isRouteActive('/ProfessionalDoctorate') }" @click="toggleMenuBar"><i class="fa-solid fa-map me-3"></i>السعودية</li>
                            </ul>
                        </li>
                        <li class="list-item">
                            <span class="span-dec relative"><i class="fa-solid fa-plane me-2"></i>الرحلات الجوية</span>
                        </li>
                        <li class="list-item">
                            <span class="span-dec relative"><i class="fa-solid fa-comments me-2"></i>أراء العملاء</span>
                        </li>
                        <li class="list-item">
                            <span class="span-dec relative"><i class="fa-solid fa-dollar-sign me-2"></i>انشئ رحتلك</span>
                        </li>
                    </ul>
                </nav>
                <button class="fa-solid fa-cart-shopping text-2xl text-primary"></button>
                <button class="fa-solid fa-user text-2xl text-primary ms-5" v-if="windowWidth < 1023.999999999999999"></button>
            </div>
        </div>
    </header>
</template>

<script>
    export default {
        name:'NavBar',
        data(){
            return{
                iconRotate1:'rotate-0',
                iconRotate2:'rotate-0',
                iconRotate3:'rotate-0',
                menubarOpen:false,
                windowWidth: window.innerWidth,
                currentRoute: '',
                subMenu1: false,
                subMenu2: false,
                subMenu3: false,
            }
        },
        methods:{
            isRouteActive(route) {
                // console.log(this.$route.fullPath);
                return this.$route.fullPath === route;
            },
            toggleMenuBar(){
                this.menubarOpen = !this.menubarOpen;
                this.closeAllSub();
            },
            updateWindowWidth() {
                this.windowWidth = window.innerWidth;
            },
            toggleSubMenu(num){
                if (num == '1') {
                    this.subMenu1= !this.subMenu1;
                    this.subMenu2= false;
                    this.subMenu3= false;
                    this.iconRotate1 = this.subMenu1 ? 'rotate-90' : 'rotate-0'
                    this.iconRotate2 = this.subMenu2 ? 'rotate-90' : 'rotate-0'
                    this.iconRotate3 = this.subMenu3 ? 'rotate-90' : 'rotate-0'
                } else if(num == '2'){
                    this.subMenu2= !this.subMenu2;
                    this.subMenu1= false;
                    this.subMenu3= false;
                    this.iconRotate1 = this.subMenu1 ? 'rotate-90' : 'rotate-0'
                    this.iconRotate2 = this.subMenu2 ? 'rotate-90' : 'rotate-0'
                    this.iconRotate3 = this.subMenu3 ? 'rotate-90' : 'rotate-0'
                }else{
                    this.subMenu3= !this.subMenu3;
                    this.subMenu2= false;
                    this.subMenu1= false;
                    this.iconRotate1 = this.subMenu1 ? 'rotate-90' : 'rotate-0'
                    this.iconRotate2 = this.subMenu2 ? 'rotate-90' : 'rotate-0'
                    this.iconRotate3 = this.subMenu3 ? 'rotate-90' : 'rotate-0'
                }
            },
            closeAllSub(){
                this.subMenu3= false;
                this.subMenu2= false;
                this.subMenu1= false;
                this.iconRotate1 = this.subMenu1 ? '-rotate-90' : 'rotate-0'
                this.iconRotate2 = this.subMenu2 ? '-rotate-90' : 'rotate-0'
                this.iconRotate3 = this.subMenu3 ? '-rotate-90' : 'rotate-0'
            },
        },
        watch: {
            $route(to) {
            // Update currentRoute when the route changes
            this.currentRoute = to.name;
            },
        },
        beforeUnmount() {
            window.removeEventListener('resize', this.updateWindowWidth);
        },
        mounted() {
            // Add a listener to update windowWidth when the window is resized
            window.addEventListener('resize', this.updateWindowWidth);
        },
    }
</script>

<style scoped>
.active{
    @apply text-primary
}

@media (max-width: 1023.999999999999999px){
.resposive-icon{
    display: block;
    margin-left: auto;
}
.ul-menu{
    position: absolute;
    top: 62px;
    left: 0;
    width: 100vw;
    /* height: 100%; */
    height: auto;
    z-index: 9999999;
    @apply bg-white block w-full text-black shadow-md
    /* display: none; */
}
.ul-menu li{
    margin-block: 20px;
    padding-block: 5px;
}
.sub-menu{
    @apply w-full relative top-2
}
.sub-menu li{
    @apply w-full static 
}

}
</style>