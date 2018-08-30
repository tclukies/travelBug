<template>
<div id='first'>
    <router-view></router-view>
        <Modal />
        <Footer />
</div>
    
</template>

<script>
import Modal from "@/components/Modal";
import Footer from "@/components/Footer";
export default {
    name: "first",
    components: {
        Modal,
        Footer
    }
};
var images = [
    "url('https://www.globotrain.ch/typo3temp/pics/21d7be9a7e.jpg')",
    "url('https://throwbackpackerblog.files.wordpress.com/2017/09/pa233512.jpg?w=1280&h=768&crop=1')",
    "url('https://s-media-cache-ak0.pinimg.com/originals/3d/4f/e6/3d4fe6bccddfd3b049ac90242bdce148.jpg')",
    "url('https://gezgin-cift.webnode.com.tr/_files/200000706-c39fcc4992/12967484_1696177410671621_2910202682994657411_o.jpg')",
    "url('https://i.pinimg.com/originals/23/e2/f8/23e2f8ecd201b4a6f772aa1e4f93a134.jpg')",
    "url('https://i.ytimg.com/vi/Xw2KcAWkHDA/maxresdefault.jpg')",
    "url('https://onelifetimetrip.com/wp-content/uploads/2018/07/NewYork.jpg')",
    "url('https://traveloregon.com/wp-content/uploads/2018/04/2018Summer_family_tramway.jpg')",
    "url('https://summitvoice.files.wordpress.com/2014/04/breck.jpg')",
    "url('https://s-ec.bstatic.com/images/hotel/max1280x900/333/33318644.jpg')",
    "url('https://cdn.allwallpaper.in/wallpapers/1280x768/15496/beautiful-switzerland-landscape-1280x768-wallpaper.jpg')",
    "url('https://cdn-images-1.medium.com/max/1280/1*K4x-LCv5mBZTgZ7UmGEynA.jpeg')",
    "url('https://wallpaper-house.com/data/out/10/wallpaper2you_458939.jpg')",
    "url('https://i.ytimg.com/vi/C317oR7HBz0/maxresdefault.jpg')",
    "url('https://wave.rozhlas.cz/sites/default/files/images/03797071.jpeg')",
    "url('https://www.telegraph.co.uk/content/dam/Travel/partnerTourImages/NewmarketHolidays/JapanLandoftheRisingSun/RESTRICTED-leadAsset-JapanLandoftheRisingSun-xlarge.png')"
];
var imageNumber = 0;
document.body.style.backgroundImage = images[imageNumber];
setInterval(() => {
    imageNumber === images.length - 1 ? (imageNumber = 0) : imageNumber++;
    document.body.style.backgroundImage = images[imageNumber];
}, 10000);
</script>

<style>
body,
html {
    height: 100vh;
    background-size: 100% auto;
    background-repeat: no-repeat;
    transition: background-image 2s;
    background: fixed;
}
</style>