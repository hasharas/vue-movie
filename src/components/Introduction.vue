<template>
  <section class="introduction">
    <div class="container">
      <h2 class="title">MOVIE LIBRARY</h2>
      <p class="description">
        Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy
        eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam
        voluptua.
      </p>
    </div>
  </section>
</template>

<style scoped>
.introduction {
  background-color: #000;
  padding: 60px 20px;
  border-top: 1px solid #242323ff;
}

.container {
  max-width: 900px;
  margin: 0;
  padding: 0 50px;
  text-align: left;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.title {
  font-size: 36px;
  margin-bottom: 20px;
  color: white;
  letter-spacing: 1px;
  text-transform: uppercase;
  font-weight: 600;
}

.description {
  font-size: 18px;
  color: #cccccc;
  line-height: 1.6;
  display: -webkit-box;
  -webkit-line-clamp: 3;
  -webkit-box-orient: vertical;
  overflow: hidden;
  text-overflow: ellipsis;
}

/* Tab */
@media screen and (max-width: 992px) {
  .container {
    padding: 50px 30px;
  }

  .title {
    font-size: 32px;
  }

  .description {
    font-size: 17px;
  }
}

/* Mobile */
@media screen and (max-width: 768px) {
  .container {
    padding: 50px 20px;
  }

  .title {
    font-size: 28px;
  }

  .description {
    font-size: 16px;
  }
}
</style>
