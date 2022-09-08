<template>
  <div id="presentation-details" class="component-content">
    <div id="presentation">
      <div class="container">
        <div class="row align-items-center" id="a-propos">
          <div class="col-md-5 ">
            <div class="container">
              <img src="../assets/woman.jpg">
            </div>
          </div>

          <div class="col-md-7">
            <div class="col-md-11">
              <h2>À propos</h2>
              <div>
                <p>
                  Je m'appelle Angélique.
                  Amoureuse des animaux depuis mon plus jeune âge, j'ai appris à les aimer et à les respecter.
                  Cependant, la vie faisant, il arrive que nous oublions nos rêves d'enfant...</p>
                <p>
                  … Mais pas tant que ça ! En 2013, je décide de prendre les choses en mains et je saisis l’opportunité
                  de vivre enfin de ma passion.
                  C’est alors que débute ma formation dans l'une des meilleures écoles de toilettage : “L'art Canin”
                  situé à Hanzinne.
                  Après avoir suivi cette formation agrémentée d'un stage régulier, j'obtiens mon diplôme avec succès et
                  j'ouvre enfin mon propre salon de toilettage le 14 octobre 2014 à Couvin.
                </p>
                <p>
                  J'ai le contact facile avec les animaux, avec qui je travaille toujours dans le calme, le respect et
                  les besoins de chacun.
                  J'adapte ma façon de travailler par rapport à l'âge, au caractère et surtout au vécu de votre chien ou
                  votre chat.
                  Mais je ne m'arrête pas là, puisque récemment j'ai ajouté à ma petite clientèle des poilus bien
                  différents : lapins et cochons d'Inde à qui je coupe régulièrement les ongles.
                  C'est donc avec plaisir que je vous recevrais, vous et votre compagnon à quatre pattes.
                </p>
              </div>
            </div>
          </div>
        </div>
      </div>

    </div>
  </div>

</template>

<script>
export default {
  name: 'about-lucky-style'
}
</script>
<style scoped>

#presentation {
  padding-top: 75px;
  padding-bottom: 50px;
  background-color: white;
  font-size: 110%;
}

@media only screen and (max-width : 767px) {
  #presentation {
    padding-top: 40px;
    padding-bottom: 50px;
  }
}

@media only screen and (max-width : 767px) {
  img {
    display: block;
    margin-left: auto;
    margin-right: auto;
    width: 50%;
    margin-bottom: 25px;
  }
}

@media only screen and (min-width : 767px) {
  img {
    width: 75%;
  }
}
img {
  border-radius: 15%;
}

.container {
  padding-right: 0;
}


h2 {
  padding-top: 0;
  padding-bottom: 30px;
}

</style>
