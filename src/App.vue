<template>
  <div>
    <nav class="navbar navbar-expand-lg bg-body-tertiary shadow" dir="rtl">
      <div class="container-fluid">
        <a class="navbar-brand fw-bold" href="#">ورزش سه</a>
        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNavDropdown"
          aria-controls="navbarNavDropdown" aria-expanded="false" aria-label="Toggle navigation">
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarNavDropdown">
          <ul class="navbar-nav">
            <li class="nav-item">
              <a class="nav-link active" aria-current="page" href="#">اخرین خبر</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="#">جدول</a>
            </li>

          </ul>
        </div>
      </div>
    </nav>
    <!-- navbar -->

    <div class="container ">
      <div class="row mt-5 " dir="rtl">
        <div class="col-lx-3 col-lg-4 col-md-6 d-flex justify-content-center" v-for="datas in data" :key="datas.title">

          <div class="card" style="width: 18rem;">
            <img src="/public/photo/n1.jpg" class="card-img-top" alt="...">
            <div class="card-body">
              <h5 style="height: 90px;" class="card-title"> {{ datas.title }} </h5>
              <p style="height: 110px;" class="card-text"> {{ datas.description }} </p>
              <a :href="datas.link" class="btn btn-primary"> مشاهده بیشتر</a>
            </div>
          </div>

        </div>


        
      </div>
    </div>





















  </div>
</template>



<script>
import axios from 'axios';

export default {
  data() {
    return {
      title:null,

      data: [],
    };
  },
  mounted() {
    axios.get('https://one-api.ir/rss/?token=305245:668d57596d425&action=varzesh3')
      .then(response => {
        this.data = response.data.result.item;
        console.log(this.data);
      })
      .catch(error => {
        console.log(error)
      })
  },
  methods:{

  }


}
</script>

<style scoped>
.card{
  margin-top: .5rem !important;
}
.card-img-top{
  width: 100%;
  height: 200px !important;
  
}
</style>