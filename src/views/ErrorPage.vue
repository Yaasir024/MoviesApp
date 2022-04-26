<template>

    <section>
      <h1>404</h1>
      <span>Page Not Found</span>

      <router-link to="/">
        <p class="back">Go Back</p>
      </router-link>
  </section>

    <div class="posters">
        <div class="poster">
            <div class="composition">
                <img src="../assets/poster1.jpeg" alt="photo 1" class="composition__photo poster1">
            </div>
            <div class="composition">
                <img src="../assets/tokyo-24.jpeg"  alt="photo 2" class="composition__photo poster2">
            </div>
            <div class="composition">
                <img src="../assets/spiderman.jpg"  alt="photo 3" class="composition__photo poster3">
            </div>
        </div>
    </div>
    <summary>
        <p>Thanks for using MoviesApp</p>
        <router-link to="/">
            <p class="back">Back Home</p>
      </router-link>
    </summary>
</template>

<script>
export default {

}
</script>

<style scoped>
    section {
        display: flex;
        align-items: center;
        justify-content: center;
        flex-direction: column;
        margin-top: 5px;
    }
    section h1 {
        font-size: 140px;
        color: #707070;
    }
    section span {
        margin-top: 20px;
        font-size: 25px;
        color: #707070;
    }
    section .back {
        margin-top: 25px;
        display: block;
        padding: 15px 25px;
        border: 1px solid #707070;
        color: #fff;
        transition: all .2s ease;
    }
    section .back:hover {
        background: #111;
        color: #707070;
    }
    .posters {
        margin-top: 100px;
        display: flex;
        align-items: center;
        justify-content: center;
    }
    .poster {
        min-height: 350px;
        width: 300px;
        position: relative;
    }
    .composition__photo {
        width: 200px;
        box-shadow: 0 1.5rem 4rem rgba(0, 0, 0, 0.4);
        border-radius: 4px;
        position: absolute;
        z-index: 5;
        transition: all .2s;
        outline-offset: 2rem; 
    }
    .poster1 {
      right: 65%;
      top: 0; 
    }
    .poster2 {
      left: 65%;
      top: 0; 
    }
    .poster3 {
      left: 20%;
      top: .9rem; 
    }
    summary {
        text-align: center;
        margin-bottom: 60px;
    }
    summary .back {
        color: #fff;
        margin-top: 10px;
    }
    summary .back:hover {
        color: #707070;
    }
</style>