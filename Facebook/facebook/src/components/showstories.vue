<template>

 <div> 
    
     <Nav></Nav>

          


<div class="container" style="padding-top: 15%">

     <router-link to="/story" class="navbar-brand" style="font-size:300%;"> Create Story </router-link>


    <div class="row">
        <div class="col-lg-12 layout-spacing">
            <div class="statbox widget box box-shadow">
                <div class="widget-header">
                    <div class="row">
                        <div class="col-xl-12 col-md-12 col-sm-12 col-12">
                            <h4 class="pb-0">Stories</h4>
                        </div>
                    </div>
                </div>
                <div class="widget-content widget-content-area">
                    <div class="row">
                        <div class="col-lg-12 col-md-12 col-sm-12">
                            <div id="content_1" class="tabcontent story-area"> 
                                <div class="story-container-1">
                                    <!-- <div class="single-create-story">
                                        <img src="https://bootdey.com/img/Content/avatar/avatar1.png" class="single-create-story-bg">
                                        <div class="create-story-author">
                                            <i class="fa fa-plus-circle fa-2x text-info"></i>
                                            <p>Create a story</p>
                                        </div>
                                    </div> -->

                                    <div class="single-story"  v-for="infe in info1" :key="infe._id" >
                                        <img :src= "'http://localhost:8000/story/get/'+ infe.url " class="single-story-bg">
                                    </div>


                                    <!-- <div class="single-story"  v-for="image in fetchedStory" >
                                       <img :src="dataUrl">
                                    </div> ghfhtfhtfhtfu-->
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div> 
</div>


</div>

</template>






<script>
import axios from "axios";
import Nav from "./Nav.vue";

export default {
  name: "showstories",
  data() {
    return {
      info1: "",
      email:"",
      fetchedStory:[],
      
    };
  },

     components:{
  Nav,
 },

  mounted() {
    this.fetchInfo1();
  },
  methods:
        {
    fetchInfo1(){
        this.email = localStorage.getItem("email");
    
        // axios.get("http://localhost:8000/story/" + this.email).then((res) => {this.info1 = res.data
        // console.log(res.data)
        // res.data.forEach(url => {
        //     axios.get("http://localhost:8000/story/get/" + url.url).then((image) => {
        //         console.log('image: ', image);
        //         this.fetchedStory.push(image);
        //     })
        // });
        // });



        axios.get("http://localhost:8000/story/" + this.email).then((res) => (this.info1 = res.data));



      
    },
    // logout() {
    //   localStorage.clear();
    //   this.$router.push("/");
    // }
  },
};
</script>





<style scoped>


body{
    background:#eee;
    margin-top:20px;
}
.widget {
    padding: 0;
    margin-top: 0;
    margin-bottom: 0;
    border-radius: 6px;
    -webkit-box-shadow: 0 4px 6px 0 rgb(85 85 85 / 8%), 0 1px 20px 0 rgb(0 0 0 / 7%), 0px 1px 11px 0px rgb(0 0 0 / 7%);
    -moz-box-shadow: 0 4px 6px 0 rgba(85, 85, 85, 0.08), 0 1px 20px 0 rgba(0, 0, 0, 0.07), 0px 1px 11px 0px rgba(0, 0, 0, 0.07);
    box-shadow: 0 4px 6px 0 rgb(85 85 85 / 8%), 0 1px 20px 0 rgb(0 0 0 / 7%), 0px 1px 11px 0px rgb(0 0 0 / 7%);
}
.widget.box .widget-header {
    background: #fff;
    padding: 0px 8px 0px;
    border-top-right-radius: 6px;
    border-top-left-radius: 6px;
}
.widget .widget-header {
    border-bottom: 0px solid #f1f2f3;
}
.widget.box .widget-header {
    background: #fff;
    padding: 0px 8px 0px;
    border-top-right-radius: 6px;
    border-top-left-radius: 6px;
}
.widget .widget-header {
    border-bottom: 0px solid #f1f2f3;
}
.widget .widget-header:after {
    clear: both;
}
.widget .widget-header:before, .widget .widget-header:after {
    display: table;
    content: "";
    line-height: 0;
}
.widget-content-area {
    padding: 20px;
    position: relative;
    background-color: #fff;
    border-bottom-left-radius: 6px;
    border-bottom-right-radius: 6px;
}
.story-container-1 {
    display: flex;
    align-items: center;
    justify-content: flex-start;
}
.story-container-1 .single-create-story {
    height: 175px;
    width: 110px;
    border-radius: 10px;
    overflow: hidden;
    position: relative;
    margin-right: 10px;
    margin-bottom: 10px;
    background: #e4e4e4;
    text-align: center;
}
img.single-create-story-bg {
    width: 100%;
    height: 120px;
    object-fit: cover;
}
.create-story-author img {
    height: 40px;
    width: 40px;
    margin-top: -20px;
    padding: 4px;
    background: #e4e4e4;
    border-radius: 50%;
}
.story-container-1 .single-story {
    height: 175px;
    width: 110px;
    border-radius: 10px;
    overflow: hidden;
    position: relative;
    margin-right: 10px;
    margin-bottom: 10px;
}
.story-container-1 .single-story::before {
    content: "";
    position: absolute;
    top: 0;
    bottom: 0;
    right: 0;
    left: 0;
    background-image: linear-gradient(rgb(255 0 0 / 0%), black);
}
img.single-story-bg {
    width: 100%;
    height: 100%;
    object-fit: cover;
}
.story-container-1 .story-author {
    position: absolute;
    top: 50%;
    left: 0px;
    transform: translateY(-50%);
    right: 0px;
    text-align: center;
    z-index: 99;
    cursor: pointer;
}

.story-author img {
    height: 60px;
    width: 60px;
    border-radius: 50%;
    border: 1px solid white;
    padding: 4px;
}

.story-container-1 .story-author p {
    color: #fff;
    width: 100%;
    margin: 5px 0px 0px 0px;
    font-weight: 600;
    font-size: 12px;
}

.create-story-author p {
    margin: 0px;
    font-size: 13px;
    font-weight: 500;
}


</style>