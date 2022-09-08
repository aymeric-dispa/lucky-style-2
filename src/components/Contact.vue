<template>
  <div id="contact-form" class="component-content" style="padding-bottom: 0">
    <div class="container">
      <h2>Contact</h2> <br/>
      <div class="row">
        <div class="col-md-8">
          <div class="map">
            <iframe
                title="Lucky-Style map"
                width="100%"
                height="300"
                style="border:0"
                loading="lazy"
                allowfullscreen
                referrerpolicy="no-referrer-when-downgrade"
                src="https://www.google.com/maps/embed/v1/place?key=AIzaSyBm6Wydfk6iDdBsVPDZA2-zC3aTbYjiCEk&q=Lucky+Style,Couvin+Belgium">
            </iframe>
          </div>
        </div>
        <div class="col-md-4">
          <div class="row">
            <div><img src="../assets/phone.svg" class="icon">
              <h6 style="padding-top: 5px"><p id="icon-txt"><strong>Numero de telephone</strong><br/>0497 31 80 99</p>
              </h6>
            </div>
          </div>
          <br/>
          <div class="row">
            <div><img src="../assets/house.svg" class="icon">
              <h6><p class="icon-txt"><strong>Addresse du salon</strong><br/>Angélique Duchêne<br/> Rue Planesse 9<br/>5660
                Couvin
              </p></h6>
            </div>

          </div>
          <div class="row">
            <a href="https://www.facebook.com/LUCKYzSTYLE/" target="_blank">
              <img class="icon" src="../assets/facebook.svg">
              <p class="icon-txt" style="padding-top: 5px">Suivez Lucky Style sur Facebook !</p></a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>

export default {
  name: 'contact-form'
}
</script>
<style scoped>
.container {
  padding-top: 60px;
  padding-bottom: 40px;
}

iframe {
  padding-bottom: 20px;
}

.icon {
  width: 50px;
  text-align: left;
  float: left;
  shape-margin: 0;
  margin-right: 5px;
}

@media only screen and (max-width : 767px) {
  img {
    display: block;
    margin-left: auto;
    margin-right: auto;
    width: 50%;
  }
}

a {
  color: black;
}

</style>
