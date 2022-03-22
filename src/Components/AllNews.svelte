<script>
  import { onMount } from "svelte";
  import axios from "axios";
  //import {endpoint} from './api.svelte';
  import Carousel from '@beyonk/svelte-carousel';

  export const endpoint = "http://api.allnigerianewspapers.com.ng/api/";
  const allnews = endpoint + "news";
  const allfashion = endpoint + "allnewsbycategory/fashion"

  let posts = [];
  let fashion = [];

  

  onMount(async function () {
    axios.all([
  axios.get(allnews),
  axios.get(allfashion),
])
.then((responseArr) => {
  
  console.log("First Post: ", responseArr[0].data.results);
  console.log("Second Comment: ", responseArr[1].data[1]);
  posts = responseArr[0].data.results;
  fashion = responseArr[1].data;
})
.catch((error) => {
  console.log(error);
});
});




  
</script>



	<!-- start block wrapper -->
  <section class="block-wrapper p-30" style="background: url(images/banner-bg.png) no-repeat center center/cover">
    <div class="container">
      <div class="row">
        <div class="col-lg-3 pr-10">

          {#each fashion.slice(1,4) as f, index }
            
         
              <div class="ts-post-overlay-style-1 ts-post-style-5">
                <div class="ts-overlay-style">
                  <div class="item">
                    <div class="ts-post-thumb">
                      <a class="post-cat ts-orange-bg" href="/">{ f.category.name }</a>
                      <a href="/">
                        <img class="img-fluid" src="{ f.image_url }" alt="">
                      </a>
                    </div>

                    <div class="overlay-post-content">
                      <div class="post-content">
                        <h3 class="post-title">
                          <a href="/">{ f.title }</a>
                        </h3>
                        <ul class="post-meta-info">
                          <li>
                            <i class="fa fa-clock-o"></i>
                            { f.uploaded }
                          </li>
                        </ul>
                      </div>
                    </div>
                  </div>
                  <!-- end item-->
                </div>
                <!-- ts overlay style end-->
              
              </div>

          {/each}

        </div>
        <!-- col end-->
        <div class="col-lg-6 pl-0 pr-10">
          <div id="featured-slider-2" class="owl-carousel ts-overlay-style ts-featured">
    
                {#each posts.slice(1,3) as n, index }
                  <div class="item" style="background-image:url({ n.image_url })">
                    <a class="post-cat ts-orange-bg" href="/">{ n.category.name }</a>
                    <div class="overlay-post-content">
                        <div class="post-content">
                            <h2 class="post-title lg">
                                <a href="/">{ n.title }</a>
                            </h2>
                            <ul class="post-meta-info">
                                <li class="author">
                                    <a href="/">
                                        <img src="http://api.allnigerianewspapers.com.ng{ n.site.logo }" alt=""> { n.site.name }
                                    </a>
                                </li>
                                <li>
                                    <i class="fa fa-clock-o"></i>
                                    { n.created_at }
                                </li>
                                <li class="active">
                                    <i class="icon-fire"></i>
                      

                                        { n.comment  }
                                    
                          
                                    
                                </li>
                            </ul>
                        </div>
                    </div>
                    <!--/ Featured post end -->

                  </div>
                {/each }
      
          </div>
          <!-- Featured owl carousel end-->
        </div>
        <!-- col end-->
        <div class="col-lg-3 pl-0">
          <div class="ts-post-overlay-style-1">
            <div class="ts-overlay-style">
              <div class="item">
                <div class="ts-post-thumb">
                  <a class="post-cat ts-blue-bg" href="/">Technology</a>
                  <a href="/">
                    <img class="img-fluid" src="images/news/tech/tech5.jpg" alt="">
                  </a>
                </div>

                <div class="overlay-post-content">
                  <div class="post-content">
                    <h3 class="post-title">
                      <a href="/">Man plans to ride out Hurricane Florence on a boat</a>
                    </h3>
                    <ul class="post-meta-info">
                      <li>
                        <i class="fa fa-clock-o"></i>
                        March 21, 2019
                      </li>
                    </ul>
                  </div>
                </div>
              </div>
              <!-- end item-->
            </div>
            <!-- ts overlay style end-->
            <div class="ts-overlay-style">
              <div class="item">
                <div class="ts-post-thumb">
                  <a class="post-cat ts-pink-bg" href="/">Music</a>
                  <a href="/">
                    <img class="img-fluid" src="images/news/music/music1.jpg" alt="">
                  </a>
                </div>

                <div class="overlay-post-content">
                  <div class="post-content">
                    <h3 class="post-title">
                      <a href="/">Tourism in Dubai is booming international tourist most visited place</a>
                    </h3>
                    <ul class="post-meta-info">
                      <li>
                        <i class="fa fa-clock-o"></i>
                        March 21, 2019
                      </li>
                    </ul>
                  </div>
                </div>
              </div>
              <!-- end item-->
            </div>
            <!-- ts overlay style end-->
          </div>
        </div>
        <!--col end-->
      </div>
    </div>
  </section>
  <!-- end  blog wrapper -->

<style>
  
</style>