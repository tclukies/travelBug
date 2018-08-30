<template>
<div id='main' >
    <router-view></router-view>
    <div class='header'>
        <Header />
    </div>
    <div class='horizontal'>
        <div class="add-and-map">
            <div>
                <AddCountry />
            </div>
            <div>
                <MapConfig />
            </div>
        </div>
        <div>
            <Locations />
        </div>
    </div>
        <Footer />
    </div>
    
</template>

<script>
import Header from "@/components/Header";
import AddCountry from "@/components/AddCountry";
import MapConfig from "@/components/MapConfig";
import Locations from "@/components/Locations";
import Footer from "@/components/Footer";
export default {
    name: "Main",
    components: {
        Header,
        AddCountry,
        MapConfig,
        Locations,
        Footer
    }
};
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
.horizontal {
    display: flex;
    margin-left: 7vh;
    margin-right: 7vh;
}
.add-and-map {
    display: flex;
    flex-flow: column;
    justify-items: center;
    align-items: center;
}
</style>

