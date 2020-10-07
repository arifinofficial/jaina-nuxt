<template>
  <div>
    <Nuxt />
  </div>
</template>

<style>
html,body{
    height: 100%; 
}

body{
    overflow-x: hidden;
    font-family: 'Poppins', sans-serif;
}

.section-default{
    padding: 2rem 0;
}

.border-radius-20{
    border-radius: 20px !important;
} 

.btn-custom{
    background-color: #B04C4C;
    box-shadow: 0px 0px 15px 2px rgba(100, 0, 0, 0.25);
    border-radius: 50px;
    color: #fff;
    font-size: 25px;
    padding: 10px 30px;
}

.bg-pink{
    background-color:#FFAAAA;
}

.bg-red{
    background-color: #B04C4C;
}

.text-orange{
    color: #F17F15 !important;
}

.text-red{
    color: #B04C4C !important;
}

.wrap-spin span{
    background-color: #fff;
    height: 6px;
    display: inline-block;
    border-radius: 10px;
}

.wrap-spin span:first-child{
    width: 30px;
    margin-right: 10px;
}

.wrap-spin span{
    width: 10px;
}

.detail-jaina .wrap-img-detail{
    box-shadow: 0px 0px 25px 2px rgba(0, 0, 0, 0.1);
    position: relative;
}

.detail-jaina .wrap-img-detail span{
    bottom: 0;
    text-align: center;
    background: rgba(176, 76, 76, 0.7);
    color: #fff;
    border-radius: 0px 0px 20px 20px;
    min-height: 50px;
    padding: 10px 2px;
}
</style>
