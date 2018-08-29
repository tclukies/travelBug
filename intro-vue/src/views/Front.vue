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
    "url('http://segundoenfoque.com/wp-content/uploads/2017/08/camboya-segundoenfoque.jpeg')",
    "url('https://www.globotrain.ch/typo3temp/pics/21d7be9a7e.jpg')",
    "url('http://master.as/wp-content/uploads/2017/06/phpFbZ12f572b5a22bcba0_1280x760.jpeg')",
    "url('https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQzlPssqEwg-xOQdgOShx9CCFY9P6sfA7ZSwMtrF0tCdQdoX4Be')",
    "url('https://i.pinimg.com/originals/3c/08/51/3c0851751eee8dd2176f23004643290f.jpg')",
    "url('https://gezgin-cift.webnode.com.tr/_files/200000706-c39fcc4992/12967484_1696177410671621_2910202682994657411_o.jpg')",
    "url('https://i.pinimg.com/originals/23/e2/f8/23e2f8ecd201b4a6f772aa1e4f93a134.jpg')",
    "url('https://i.ytimg.com/vi/Xw2KcAWkHDA/maxresdefault.jpg')",
    "url('http://www.freedomtourtravel.com/wp-content/uploads/2014/11/Castle-San-Angelo.jpg')",
    "url('https://traveloregon.com/wp-content/uploads/2018/04/2018Summer_family_tramway.jpg')",
    "url('https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRUOSFVSkcAWb03LR4Voao2b3FaNhSa7-esNDhQWDqZlhfUXiEm')",
    "url('http://5b0988e595225.cdn.sohucs.com/images/20171121/5c43a86205ce43cba5a0bf813afede38.jpeg')",
    "url('https://summitvoice.files.wordpress.com/2014/04/breck.jpg')",
    "url(https://s-ec.bstatic.com/images/hotel/max1280x900/333/33318644.jpg')",
    "url('https://wave.rozhlas.cz/sites/default/files/images/03797071.jpeg')",
    "url('http://www.landchallenge.pt/wp-content/uploads/2016/09/img-02.jpg')",
    "url('http://thaiis.net/wp-content/thumb/thumb.php?src=http://thaiis.net/mayalay/wp-content/uploads/sites/2/2013/11/overview-mayalay-beach-koh-ngai-thailand-03.jpg&w=1280&h=760&zc=1')"
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
    transition: background-image 3s;
    background: fixed;
}
</style>