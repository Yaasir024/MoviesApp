<template>
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
        <p>
        <router-link to="/">
            <p class="back">MoviezApp</p>
      </router-link> One stop entertainment Database</p>
        
    </summary>
</template>

<script>
export default {

}
</script>

<style scoped>
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
        display: inline;
    }
    summary .back:hover {
        color: #707070;
    }
</style>