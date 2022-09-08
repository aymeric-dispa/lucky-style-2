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
        <br/>
        <h3>Liste des prix</h3>
        Veuillez selectionner le service dont votre animal a besoin ci-dessous afin d'afficher le prix correspondant
      </div>
      <div class="accordion" id="pricingAccordion">
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
              <p style="padding-left: 10px">
                {{ price.text }}
              </p>
            </div>
          </div>
        </template>
      </div>
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
  {differentiator: dogSizes.MINI.valueOf(), prix: "à partir de 32€*"},
  {differentiator: dogSizes.SMALL.valueOf(), prix: "à partir de 37€*"},
  {differentiator: dogSizes.MEDIUM.valueOf(), prix: "à partir de 42€*"},
  {differentiator: dogSizes.BIG.valueOf(), prix: "à partir de 57€*"},
  {differentiator: dogSizes.HUGE.valueOf(), prix: "à partir de 67€*"},
  {differentiator: dogSizes.COCKER.valueOf(), prix: "à partir de 52€*"},
];

const bath = [
  {differentiator: dogSizes.MINI.valueOf(), prix: "35€/h"},
  {differentiator: dogSizes.SMALL.valueOf(), prix: "35€/h"},
  {differentiator: dogSizes.MEDIUM.valueOf(), prix: "35€/h"},
  {differentiator: dogSizes.BIG.valueOf(), prix: "35€/h"},
  {differentiator: dogSizes.HUGE.valueOf(), prix: "35€/h"}
];

const cut = [
  {differentiator: dogSizes.SMALL.valueOf(), prix: "de 42€ à 52€*"},
  {differentiator: dogSizes.MEDIUM.valueOf(), prix: "de 52€ à 62€*"},
  {differentiator: dogSizes.BIG.valueOf(), prix: "à partir de 77€*"},
  {differentiator: dogSizes.HUGE.valueOf(), prix: "35€/h"}
];
const trimming = [
  {differentiator: dogSizes.SMALL.valueOf(), prix: "35€/h"},
  {differentiator: dogSizes.MEDIUM.valueOf(), prix: "35€/h"},
  {differentiator: dogSizes.BIG.valueOf(), prix: "35€/h"},
  {differentiator: dogSizes.HUGE.valueOf(), prix: "35€/h"}
];
const other = [
  {differentiator: "Coupe des ongles", prix: "de 5€ à 10€"},
  {differentiator: "Chats et autres toilettages", prix: "30€/h"}
];

const cocker = [
  {differentiator: "Dos trimmer", prix: "62€"},
  {differentiator: "Dos tondu", prix: "57€"}
];

const prices = [
  {
    priceInfo: tonte,
    name: "Tonte",
    differentiator: "Taille",
    text: "*des frais additionnels équivalents au tarif horaire (35€/h) seront demandés en cas de travail supplémentaire."
  },
  {priceInfo: bath, name: "Bain et démelage", differentiator: "Taille"},
  {
    priceInfo: cut,
    name: "Coupe ciseaux",
    differentiator: "Taille",
    text: "*des frais additionnels équivalents au tarif horaire (35€/h) seront demandés en cas de travail supplémentaire."
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
  background: rgba(218, 241, 186, 0.8);
}

.pricing-txt {
  font-family: 'GothamRounded-Light', sans-serif;
  padding-top: 60px;
  padding-bottom: 25px;
  font-size: 110%;
}

.table {
  --bs-table-hover-bg: rgba(255, 230, 252, 0.90);
  --bs-table-striped-bg: rgba(255, 230, 252, 0.40);
}


h2, h3 {
}

</style>
