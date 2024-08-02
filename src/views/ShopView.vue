<template>
    <!-- Start Product Section -->
    <div class="product-section">
        <div class="container">
            <div class="row">

                <!-- Start Column 1 -->
                <div class="col-md-12 col-lg-3 mb-5 mb-lg-0">
                    <h2 class="mb-4 section-title">Crafted with excellent material.</h2>
                    <p class="mb-4">Donec vitae odio quis nisl dapibus malesuada. Nullam ac aliquet velit. Aliquam vulputate velit imperdiet dolor tempor tristique. </p>
                    <p><a href="shop.html" class="btn">Explore</a></p>
                </div> 
                <!-- End Column 1 -->

                <!-- Start Column-->
                <!-- @foreach ($best_products as $product ) -->
                <div class="col-12 col-md-4 col-lg-3 mb-5 mb-md-0" v-if="productDatas" v-for="(item, index) in productDatas" :key="index">
                    <a class="product-item" href="javascript:void(0);">
                        <img :src="item.img_link" alt="Image" class="img-fluid product-thumbnail">
                        <h3 class="product-title">{{ item.name }}</h3>
                        <strong class="product-price">{{ item.price }}</strong>

                        <span class="icon-cross">
                            <img src="../assets/images/cross.svg" class="img-fluid">
                        </span>
                    </a>
                </div>
                <div class="col-12 col-md-4 col-lg-3 mb-5 mb-md-0" v-else>
                    <h5 class="text-center">Product Not Found</h5>
                </div>

                <!-- @endforeach -->
                <!-- End Column -->

            </div>
        </div>
    </div>
    <!-- End Product Section -->
</template>

<script>
import axios from "axios";

export default {
    data(){
        return {
            productDatas: null,
            apiProductUrl: 'https://furni-store.kihub.net/api/products?limit=10',
        }
    },
    mounted() {
        console.log(this.productDatas)
        if (!this.productDatas) {
            this.fetchData();
        }
    },
    methods: {
        async fetchData() {
            try {
                const productResponse = await axios.get(this.apiProductUrl);
                this.productDatas = productResponse.data.datas;
            } catch (error) {
                console.error('Error fetching data:', error);
            }
        }
    }
}
</script>