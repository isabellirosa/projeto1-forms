<script setup>

</script>

<template>
  <div class="main">
    <img src="../src/perfil (2).png" width="40px">
    <h1>Perfil</h1>
    <form class="row g-4">
  <div class="col-md-5">
    <input type="text" class="form-control" id="inputEmail4" placeholder="nome">
  </div>
  <div class="col-md-5">
    <input type="text" class="form-control" id="inputPassword4" placeholder="sobrenome">
  </div>
  <div class="col-md-2">
    <input type="number" class="form-control" id="inputPassword4" placeholder="idade">
  </div>
  <div class="col-4">
    <input type="email" class="form-control" id="inputEmail4" placeholder="email">
  </div>
  <div class="col-md-4">
    <input type="password" class="form-control" id="inputPassword4" placeholder="insira sua senha">
  </div>
  <div class="col-md-4">
    <input type="password" class="form-control" id="inputPassword4" placeholder=" confirme sua senha">
  </div>
  <div class="col-md-2">
    <input type="text" class="form-control" id="inputZip"  placeholder="CEP">
  </div>
  <div class="col-md-4">
    <select id="inputState" class="form-select"  placeholder="estado">
      <option selected>Estado</option>
      <option>...</option>
    </select>
  </div> 
  <div class="col-md-6">
    <input type="text" class="form-control" id="inputCity"  placeholder="cidade">
  </div>
  
  <div class="col-4">
    <textarea cols="35" rows="6" placeholder="Biografia"/>
  </div>
  <div class="col-2 ">
    <h1 class="categorias">Hobbies:</h1>
    <div class="form-check">
  <input class="form-check-input" type="checkbox" name="esportes" id="esportes">
  <label class="form-check-label" for="esportes">
    Esportes
  </label>
</div>
<div class="form-check">
  <input class="form-check-input" type="checkbox" name="ler" id="ler">
  <label class="form-check-label" for="ler">
    Ler
  </label>
</div>
<div class="form-check">
  <input class="form-check-input" type="checkbox" name="esportes" id="esportes">
  <label class="form-check-label" for="esportes">
    Esportes
  </label>
</div>
<div class="form-check form-check-inline">
  <input class="form-check-input" type="checkbox" name="esportes" id="esportes">
  <label class="form-check-label" for="esportes">
    Esportes
  </label>
</div>
  </div>
  
  <div class="col-2 ">
    <h1 class="categorias">Best language:</h1>
    <div class="form-check">
  <input class="form-check-input" type="radio" name="esportes" id="esportes">
  <label class="form-check-label" for="esportes">
    Esportes
  </label>
</div>
<div class="form-check">
  <input class="form-check-input" type="radio" name="ler" id="ler">
  <label class="form-check-label" for="ler">
    Ler
  </label>
</div>
<div class="form-check">
  <input class="form-check-input" type="radio" name="esportes" id="esportes">
  <label class="form-check-label" for="esportes">
    Esportes
  </label>
</div>
<div class="form-check form-check-inline">
  <input class="form-check-input" type="radio" name="esportes" id="esportes">
  <label class="form-check-label" for="esportes">
    Esportes
  </label>
</div>
  </div>
  <div class="col-4">
    <div class="form-check">
      <label class="form-check-label" for="inputGroupFile01">Foto de perfil:</label>
      <input type="file" class="form-control" id="inputGroupFile01">
      <button type="submit" class="btn btn-primary">Enviar</button>
    </div>
  </div>
</form>
  </div>
</template>

<style scoped>
h1{
  color:white;
  display: inline;
}
img{
  margin-bottom:20px;
  margin-right: 13px;
}
.categorias{
  color:rgb(59, 59, 59);
  font-size: medium;
}
.biografia{
  height: 300px;
}
.main{
  position: absolute; 
  top: 50%; 
  left: 50%; 
  transform: translate(-50%, -50%); 
  padding: 30px;
  border: 3px solid white;
  border-radius: 10px;
  background-color: rgba(240, 248, 255, 0.459);
  width: 1000px;
}
#inputGroupFile01{
  margin-top: 10px;
}
.btn{
  width:170px;
  border-radius: 10px;
  border: 2px solid white;
  color: rgb(41, 40, 40);
  font-weight:500;
  background-color: rgba(195, 81, 247, 0.459);
  margin-top:20px;
  margin-left: 20%;
}
</style>
