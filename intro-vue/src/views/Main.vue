<template>
<div id='main' >
    <router-view></router-view>
    <div class='header'>
    <Header />
    </div>
    <div class='horizontal'>
    <div>
    <AddCountry />
    </div>
    <div>
    <Locations />
    </div>
    <div>
    <MapConfig />
    </div>
    </div>
    <Footer />
    </div>
    
</template>

<script>
import Header from "@/components/Header";
import AddCountry from "@/components/AddCountry";
import Locations from "@/components/Locations";
import MapConfig from "@/components/MapConfig";
import Footer from "@/components/Footer";
export default {
    name: "Main",
    components: {
        Header,
        AddCountry,
        Locations,
        MapConfig,
        Footer
    }
};
</script>

<style>
.main,
html {
    background-image: url("https://blenderartists.org/uploads/default/original/4X/9/d/d/9dd7ee0b61133075aaf60207c9c05ebc1ac23cad.jpg");
}
</style>

