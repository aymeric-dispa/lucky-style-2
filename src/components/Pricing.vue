<template>
  <div class="component-content" id="pricing">
    <div class="container pricing-txt">
      <div class="col-md-11 col-sm-12 col-centered ">
        <h2>Services et tarifs</h2>
        Tous les compagnons sont les bienvenus, du plus petit au plus grand.

        J'utilise des shampoings haut de gamme Diamex, prévus pour respecter le type de peau et poils de chaque chien.
        <p><br/>
          Vous ne savez pas vous déplacer ?
          Le transport de votre animal peut être arrangé (des frais supplémentaires seront appliqués).
        </p>
        Les tarifs diffèrent en fonction de l'espèce de l'animal, du type de soin à effectuer ainsi que de sa
        race/taille :
        <ul>
          <li>Mini: York toy, Chihuahua</li>
          <li>Petite race: Bichon, Shih-tzu, Yorkshire, Jack Russel...</li>
          <li>Moyenne race: Cocker, Cavalier King Charles, Schauzer moyen...</li>
          <li>Grande race: Retriever, Bergers, Colley, Border Collie, Husky...</li>
          <li>Très Grande race: Terre Neuve, Bouvier Bernois, Montagne des pyrénées...</li>
        </ul>
        <h3>Liste des prix</h3>
        Veuillez selectionner le service dont votre animal a besoin ci-dessous afin d'afficher le prix correspondant
      </div>
      <div class="accordion" id="pricingAccordion" >
        <template v-for="price in prices" :key="price.name">
          <div class="accordion-item">
            <h2 class="accordion-header">
              <button class="accordion-button collapsed" type="button" data-bs-toggle="collapse"
                      v-bind:data-bs-target="'#'+price.name.replace(/\s+/g, '-')+'collapse'" aria-expanded="false"
                      aria-controls="collapseOne">
                <h5>{{ price.name }}</h5>
              </button>
            </h2>
            <div v-bind:id="price.name.replace(/\s+/g, '-')+'collapse'" class="accordion-collapse collapse"
                 aria-labelledby="headingOne"
                 data-bs-parent="#accordionExample">
              <table class="table table-hover table-striped">
                <thead>
                <tr>
                  <th scope="col">{{ price.differentiator }}</th>
                  <th scope="col">Prix</th>
                </tr>
                </thead>
                <tbody>
                <template v-for="item in price.priceInfo " :key="item.id">
                  <tr>
                    <td>{{ item.differentiator }}</td>
                    <td>{{ item.prix }}</td>
                  </tr>
                </template>
                </tbody>
              </table>
              <p style="padding-left: 10px" v-html="price.text"></p>
            </div>
          </div>
        </template>
      </div>
      <p style="padding-top: 10px">
        <strong>⚠️ Un supplément sur le toilettage pourra être demandé en cas de rendez-vous non honoré.</strong>
      </p>
    </div>
  </div>
</template>

<script>
const dogSizes = {
  MINI: 'Mini race',
  SMALL: 'Petite race',
  MEDIUM: 'Moyenne race',
  BIG: 'Grande race',
  HUGE: 'Très grande race',
  COCKER: 'Cocker'
};


const tonte = [
  {differentiator: dogSizes.MINI.valueOf(), prix: "à partir de 35€"},
  {differentiator: dogSizes.SMALL.valueOf(), prix: "à partir de 40€"},
  {differentiator: dogSizes.MEDIUM.valueOf(), prix: "à partir de 45€"},
  {differentiator: dogSizes.BIG.valueOf(), prix: "à partir de 60€"},
  {differentiator: dogSizes.HUGE.valueOf(), prix: "à partir de 70€"},
  {differentiator: dogSizes.COCKER.valueOf(), prix: "de 45€ à 57€"},
];

const bath = [
  {differentiator: dogSizes.MINI.valueOf(), prix: "35€/h"},
  {differentiator: dogSizes.SMALL.valueOf(), prix: "35€/h"},
  {differentiator: dogSizes.MEDIUM.valueOf(), prix: "40€/h"},
  {differentiator: dogSizes.BIG.valueOf(), prix: "40€/h"},
  {differentiator: dogSizes.HUGE.valueOf(), prix: "40€/h"}
];

const cut = [
  {differentiator: dogSizes.SMALL.valueOf(), prix: "de 45€ à 55€*"},
  {differentiator: dogSizes.MEDIUM.valueOf(), prix: "de 55€ à 65€*"},
  {differentiator: dogSizes.BIG.valueOf(), prix: "40€/h"},
  {differentiator: dogSizes.HUGE.valueOf(), prix: "40€/h"}
];
const trimming = [
  {differentiator: dogSizes.SMALL.valueOf(), prix: "35€/h"},
  {differentiator: dogSizes.MEDIUM.valueOf(), prix: "40€/h"},
  {differentiator: dogSizes.BIG.valueOf(), prix: "40€/h"},
  {differentiator: dogSizes.HUGE.valueOf(), prix: "40€/h"}
];
const other = [
  {differentiator: "Coupe des ongles", prix: "de 5€ à 10€"},
  {differentiator: "Toilettage chat et NAC", prix: "35€/h"}
];

const cocker = [
  {differentiator: "Dos trimmer", prix: "65€"},
  {differentiator: "Dos tondu", prix: "60€"},
  {differentiator: "Tonte", prix: "de 45€ à 57€"}
];

const prices = [
  {
    priceInfo: tonte,
    name: "Tonte",
    differentiator: "Taille",
    text: "*Des frais additionnels équivalents au tarif horaire (apd. 35€/h) seront facturés en cas de travail supplémentaire."
  },
  { priceInfo: bath,
    name: "Bain et démelage",
    differentiator: "Taille",
    text: ["*Des frais additionnels équivalents au tarif horaire (apd. 35€/h) seront facturés en cas de travail supplémentaire.",
        "En cas d'utilisation de shampoing anti-puce, des frais additionnels de 3€ à 10€ (selon la taille) seront appliqués si nécessaire."].join('<br>')
  },
  {
    priceInfo: cut,
    name: "Coupe ciseaux",
    differentiator: "Taille"
  },
  {priceInfo: trimming, name: "Trimming", differentiator: "Taille"},
  {priceInfo: cocker, name: "Cocker", differentiator: "Service"},
  {priceInfo: other, name: "Autre", differentiator: "Service"}
]

export default {
  name: 'pricing-grid',
  data() {
    return {
      animal: null,
      ssize: null,
      sizes: dogSizes,
      tonte: tonte,
      bath: bath,
      cut: cut,
      trimming: trimming,
      cocker: cocker,
      other: other,
      prices: prices
    }
  }
}
</script>

<style scoped>

#pricing{
  background: rgba(199, 216, 250, 0.8);
}

.pricing-txt {
  font-family: 'GothamRounded-Light', sans-serif;
  padding-top: 60px;
  padding-bottom: 25px;
  font-size: 110%;
}

.table {
  --bs-table-hover-bg: rgba(232, 230, 255, 0.9);
  --bs-table-striped-bg: rgba(235, 230, 255, 0.4);
}


h2, h3 {
}

</style>
