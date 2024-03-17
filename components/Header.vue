<template>
  <header class="header">
    <div class="left-group">
      <div class="logo">
        <img src="/images/logo.png" alt="Logo" />
      </div>
      <div class="location-display">
        <span class="location-label">Paikkakunta</span>
        <div class="location-name">Helsinki
          <img src="/images/arrow.svg" alt="Arrow down" class="arrow-icon" />
        </div>
      </div>
      <div class="location-display">
        <span class="location-label">Hoito tai palvelu</span>
        <div class="service-name">Klassinen Hieronta
          <img src="/images/arrow.svg" alt="Arrow down" class="arrow-icon" />
        </div>
      </div>
    </div>
    <div class="professional-link">
      Ammattilaisille
      <img src="/images/arrow.svg" alt="Arrow down" class="arrow-icon" />
    </div>
  </header>
</template>

<script setup>
</script>
<style lang="scss" scoped>

  .header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1rem;
    background-color: #f8f8f8;
    width: 100%;
    color: black;
    border: 1px solid #000;
  }

  .left-group {
    display: flex;
    justify-content: space-between;
    width: 30%;
  }

  .logo img {
    height: 50px;
  }

  .location-display {
    display: flex;
    flex-direction: column;
    margin-left: 20px;
  }

  .location-label {
    font-size: 0.9em;
    margin-bottom: 5px;
  }

  .location-name,
  .service-name {
    font-weight: bold;
    margin-right: 20px;
  }

  .professional-link {
    padding: 8px 20px;
    background-color: white;
    color: black;
    border-radius: 15px;
    border: 1px solid #ccc;
    cursor: pointer;
  }

  .arrow-icon {
    margin-left: 0.5rem;
    width: 16px;
    height: auto;
  }
  @media (max-width: 1350px) {
    .left-group {
      width: 60%;
    }
  }
  @media (max-width: 1050px) {
    .left-group {
      width: 60%;
    }
  }
  @media (max-width: 740px) {
    .left-group {
      width: 80%;
    }
  }
  @media (max-width: 620px) {
    .location-display {
      display: none;
    }
  }
</style>
