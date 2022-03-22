<script>
    import { onMount } from "svelte";
    import axios from "axios";
    import {endpoint} from '../Components/api.svelte';
    import MarqueeTextWidget from "svelte-marquee-text-widget";
  
    const scrolldata = endpoint + "allnewsbycategory/politics";
    
    //console.log(scrolldata)
    let scroll = [];
  
    
  
    onMount(async function () {
        try {
          const response = await axios.get(scrolldata);
          scroll = response.data;
          //console.log(scroll);
        } catch (error) {
          console.error(error);
        }
    });
  
    //let today = new Date();
    //let  date = today.getFullYear()+'-'+(today.getMonth()+1)+'-'+today.getDate();
    //document.getElementById("currentDate").value = date;
    
   
  </script>
  
<!-- top bar start -->
    <section class="top-bar v4">
        <div class="container">
            <div class="row">
                <div class="col-md-8 align-self-center">
                    <div class="ts-breaking-news clearfix">
                        <h2 class="breaking-title float-left">
                            <i class="fa fa-bolt"></i> Breaking News Update:</h2>
                        <div class="breaking-news-content float-left" id="breaking_slider1">

                           {#each scroll.slice(1,6)  as s, index }

                                <div class="breaking-post-content">
                                    <p>
                                        <a href="/">{s.title}</a>
                                    </p>
                                </div>
                                
                            {/each}


                                <!-- simple marquee text -->

                           
                              


                           
                        </div>
                    </div>
                </div>
                <!-- end col-->

                <div class="col-md-4 align-self-center">
                    <div class="text-right xs-left">
                        <div class="ts-date-item" id="currentDate">
                            <i class="fa fa-clock-o"></i> </div>
                    </div>

                </div>
                <!--end col -->


            </div>
            <!-- end row -->
        </div>
    </section>
    <!-- end top bar-->

    <section class="header-middle">
        <div class="container">
          <div class="row">
            <div class="col-md-4 align-self-center">
              <div class="header-logo">
                <a href="/">
                  <img src="./frontend/images/logo/allnigerianewspaper_logo.png" alt="All Nigeria NewsPaper" width="200px" height="57px">
                </a>
              </div>
            </div>
            <div class="col-md-8 align-self-center">
              <div class="banner-imgr">
                <a href="/">
                  <img class="img-fluid" src="./frontend/images/banner/banner2.jpg" alt="">
                </a>
              </div>
            </div>
            <!-- col end -->
          </div>
          <!-- row  end -->
        </div>
        <!-- container end -->
      </section>
