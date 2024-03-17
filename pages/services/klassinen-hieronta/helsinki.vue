<template>
  <div class="container">
    <header class="header">
      <h1>Klassinen hieronta</h1>
      <span>7 palveluntarjoajaa alueella</span>
    </header>
    <main class="content">
      <section class="service-list">
        <ServiceCard
          v-for="provider in providers"
          :key="provider.id"
          :provider="provider"
        />
      </section>
      <aside class="sidebar">
        <section class="service-info">
          <h2>Onko hieronta oikea valinta?</h2>
          <p>Hieronta on tarpeen silloin, kun vaivana on niska-hartiaseudun kivut ja jännitykset. Hieroja avaa lihasjumeja hieromalla – johtuivatpa ne sitten treenaamisesta tai liiasta tietokoneen äärellä istumisesta. Hieronta rentouttaa lihaksia ja laittaa niissä olevat kuona-aineet liikkeelle. Hieronnassa voi myös käydä ennen urheilusuoritusta tai sen jälkeen, jotta lihakset rentoutuisivat ja kroppa palautuisi paremmin. Jos kuitenkin niska-hartiaseudun oireisiin liittyy päänsärkyä, huimausta tai käden puutumista, käy ensin lääkärin vastaanotolla selvittämässä, ovatko vaivat lihasperäisiä vai merkki jostain muusta ongelmasta.</p>
        </section>
        <section class="additional-services">
          <h3>Hae muita palveluita samalta alueelta</h3>
          <ul>
            <NuxtLink v-slot="{ navigate }" to="/services/osteopatia/helsinki" custom>
            <li @click="navigate">
              <span class="icon">🔍</span>
              <div class="service-description">
                <strong >Osteopatia</strong>
                <p>Koko kroppa jumissa? Osteopaatti hoitaa kokonaisvaltaisesti</p>
              </div>
            </li>
          </NuxtLink>
          <NuxtLink v-slot="{ navigate }" to="/services/fysioterapia/helsinki" custom>
            <li @click="navigate">
              <span class="icon">🔍</span>
              <div class="service-description">
                <strong>Fysioterapia</strong>
                <p>Kipeä selkä, polvi tai olkapää? Fysioterapeutti löytää kivun syyn ja neuvoo kotitreenit.</p>
              </div>
            </li>
          </NuxtLink>
          </ul>
        </section>
      </aside>
    </main>
  </div>
</template>

<script setup>
import ServiceCard from '~/components/Card.vue'
import { ref } from 'vue'

const providers = ref([]);

onMounted(async () => {
  const response = await fetch('http://localhost:3001/providers');
  providers.value = await response.json();
});
</script>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  max-width: 1200px;
  margin: 0 auto;
}

.header {
  text-align: left;
  width: 100%;
  padding: 1rem;
  margin-top: 2rem;
  margin-bottom: 2rem;
}

@media (max-width: 1250px) {
  .content {
    flex-direction: column;
  }
  
  .header {
    width: 100%;
    align-items: flex-start;
    margin-top: 1rem;
    padding: 0 1rem;
  }

  .service-list {
    grid-template-columns: 1fr; 
  }

  .sidebar {
    width: calc(100% - 8rem) !important;
    margin: 1rem;
    order: -1;
  }
}

@media (max-width: 862px) {
  .service-list {
    grid-template-columns: 1fr;
    justify-content: center;
    margin: 1rem auto; 
  }

  .sidebar {
    width: 100%;
    margin: 1rem 0;
    order: -1;
  }

  .content {
    justify-content: center;
  }
}

@media (min-width: 768px) {
  .header {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    padding-left: 5%;
  }
}

.content {
  margin-top: 4rem; 
  width: 100%; 
  max-width: 1200px; 
  margin-left: auto;
  margin-right: auto;
  display: flex; 
  flex-wrap: wrap; 
  justify-content: space-around; 
  align-items: flex-start;
}

.service-list {
  display: grid;
  width: 100%;
  grid-template-columns: repeat(auto-fit, 400px);
  flex: 1;
  gap: 1rem;
  margin: 1rem;
}

.sidebar {
  width: 300px;
  margin-left: 2rem;
  flex-shrink: 0;
}

.service-info {
  margin-bottom: 2rem;
}
.additional-services {
  border-top: 2px solid #000; 
  padding-top: 2rem; 
  margin-top: 2rem; 
}

.additional-services h3 {
  margin-bottom: 1rem;
}

.additional-services ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.additional-services ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.additional-services li {
  display: flex;
  align-items: center;
  margin-bottom: 1rem;
}

.icon {
  margin-right: 0.5rem;
  display: inline-block;
}

.service-description {
  margin-left: 0.5rem;
}

.service-description strong {
  display: block; 
  margin-bottom: 0.25rem;
}
</style>
