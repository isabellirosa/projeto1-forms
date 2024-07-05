<script setup>
import { ref } from 'vue'
const enviado = ref(false)

function enviar() {
  enviado.value = true
}

const usuario = ref(
  {
    nome: '',
    sobrenome: '',
    idade: '',
    senha: '',
    cep: '',
    estado: '',
    cidade: '',
    biografia: '',
    hobbies: [],
    linguagem: '',
    avatar: ''
  }
)
const estados = [
  { sigla: 'AC', nomeEstado: 'Acre' },
  { sigla: 'AL', nomeEstado: 'Alagoas' },
  { sigla: 'AP', nomeEstado: 'Amapá' },
  { sigla: 'AM', nomeEstado: 'Amazonas' },
  { sigla: 'BA', nomeEstado: 'Bahia' },
  { sigla: 'CE', nomeEstado: 'Ceará' },
  { sigla: 'DF', nomeEstado: 'Distrito Federal' },
  { sigla: 'ES', nomeEstado: 'Espírito Santo' },
  { sigla: 'GO', nomeEstado: 'Goiás' },
  { sigla: 'MA', nomeEstado: 'Maranhão' },
  { sigla: 'MT', nomeEstado: 'Mato Grosso' },
  { sigla: 'MS', nomeEstado: 'Mato Grosso do Sul' },
  { sigla: 'MG', nomeEstado: 'Minas Gerais' },
  { sigla: 'PA', nomeEstado: 'Pará' },
  { sigla: 'PB', nomeEstado: 'Paraíba' },
  { sigla: 'PR', nomeEstado: 'Paraná' },
  { sigla: 'PE', nomeEstado: 'Pernambuco' },
  { sigla: 'PI', nomeEstado: 'Piauí' },
  { sigla: 'RJ', nomeEstado: 'Rio de Janeiro' },
  { sigla: 'RN', nomeEstado: 'Rio Grande do Norte' },
  { sigla: 'RS', nomeEstado: 'Rio Grande do Sul' },
  { sigla: 'RO', nomeEstado: 'Rondônia' },
  { sigla: 'RR', nomeEstado: 'Roraima' },
  { sigla: 'SC', nomeEstado: 'Santa Catarina' },
  { sigla: 'SP', nomeEstado: 'São Paulo' },
  { sigla: 'SE', nomeEstado: 'Sergipe' },
  { sigla: 'TO', nomeEstado: 'Tocantins' }
]
function handleFileUpload(e) {
  const target = e.target
  console.log(target)
  if (target && target.files) {
    const file = target.files[0]
    usuario.value.avatar = URL.createObjectURL(file)
  }
}
</script>

<template>
  <div class="main">
    <!-- <div v-if="enviado">
      <img v-if="usuario.avatar" class="avatar" :src="usuario.avatar" />
      <p v-for="(value, key) of usuario" :key="key">{{ key }}: {{ value }}</p>
    </div> -->
    <div class="perfil-usuario" v-if="enviado">
      <section class="informacoes-principais">
        <img v-if="usuario.avatar" class="avatar" :src="usuario.avatar" />
        <div class="nome-email">
        <h1>{{usuario.nome}}</h1>
        <h2>{{usuario.sobrenome}}</h2>
        <h3>{{usuario.email}}</h3>
      </div>
      </section>
      
      <p v-for="(value, key) of usuario" :key="key">{{ key }}: {{ value }}</p>
    </div>
    <div v-else>
      <img src="../src/perfil (2).png" width="40px">
      <h1>Perfil</h1>
      <form @submit.prevent="enviar()" validate class="row g-4">
        <div class="col-md-5">
          <input v-model="usuario.nome" type="text" class="form-control" id="inputEmail4" placeholder="nome">
        </div>
        <div class="col-md-5">
          <input v-model="usuario.sobrenome" type="text" class="form-control" id="inputPassword4" placeholder="sobrenome">
        </div>
        <div class="col-md-2">
          <input v-model="usuario.idade" type="number" class="form-control" id="inputPassword4" placeholder="idade">
        </div>
        <div class="col-4">
          <input v-model="usuario.email" type="email" class="form-control" id="inputEmail4" placeholder="email">
        </div>
        <div class="col-md-4">
          <input v-model="usuario.senha" type="password" class="form-control" id="inputPassword4"
            placeholder="insira sua senha">
        </div>
        <div class="col-md-4">
          <input type="password" class="form-control" id="inputPassword4" placeholder=" confirme sua senha">
        </div>
        <div class="col-md-2">
          <input v-model="usuario.cep" type="text" class="form-control" id="inputZip" placeholder="CEP">
        </div>
        <div class="col-md-4">
          <select v-model="usuario.estado" id="inputState" class="form-select" placeholder="estado">
            <option selected disabled>Estado</option>
            <option v-for="option in estados" :key="option">
              {{ option.sigla }}
            </option>
          </select>
        </div>
        <div class="col-md-6">
          <input v-model="usuario.cidade" type="text" class="form-control" id="inputCity" placeholder="cidade">
        </div>

        <div class="col-4">
          <textarea v-model="usuario.biografia" cols="35" rows="6" placeholder="Biografia" class="form-control" />
        </div>
        <div class="col-2 ">
          <h1 class="categorias">Hobbies:</h1>
          <div class="form-check">
            <input v-model="usuario.hobbies" class="form-check-input" type="checkbox" name="esportes" value="Esportes">
            <label class="form-check-label" for="esportes">
              Esportes
            </label>
          </div>
          <div class="form-check">
            <input v-model="usuario.hobbies" class="form-check-input" type="checkbox" name="ler" value="Ler">
            <label class="form-check-label" for="ler">
              Ler
            </label>
          </div>
          <div class="form-check">
            <input v-model="usuario.hobbies" class="form-check-input" type="checkbox" name="cozinhar" value="Cozinhar">
            <label class="form-check-label" for="cozinhar">
              Cozinhar
            </label>
          </div>
          <div class="form-check form-check-inline">
            <input v-model="usuario.hobbies" class="form-check-input" type="checkbox" name="games" value="Games">
            <label class="form-check-label" for="games">
              Games
            </label>
          </div>
        </div>

        <div class="col-2 ">
          <h1 class="categorias">Best language:</h1>
          <div class="form-check">
            <input v-model="usuario.linguagem" class="form-check-input" type="radio" name="language" value="Python">
            <label class="form-check-label" for="language">
              Python
            </label>
          </div>
          <div class="form-check">
            <input v-model="usuario.linguagem" class="form-check-input" type="radio" name="language" value="PHP">
            <label class="form-check-label" for="language">
              PHP
            </label>
          </div>
          <div class="form-check">
            <input v-model="usuario.linguagem" class="form-check-input" type="radio" name="language" value="Java">
            <label class="form-check-label" for="language">
              Java
            </label>
          </div>
          <div class="form-check form-check-inline">
            <input v-model="usuario.linguagem" class="form-check-input" type="radio" name="language" value="Javascript">
            <label class="form-check-label" for="language">
              Javascript
            </label>
          </div>
        </div>
        <div class="col-4">
          <div class="form-check">
            <label class="form-check-label" for="inputGroupFile01">Foto de perfil:</label>
            <input type="file" class="form-control" id="inputGroupFile01" @change="handleFileUpload($event)">
            <button @click="enviar()" type="submit" class="btn btn-primary">Enviar</button>
          </div>
        </div>
      </form>
    </div>
  </div>
</template>
"
<style scoped>
h1 {
  color: white;
  display: inline;
}

img {
  width: 150px;
  border-radius: 50%;
  margin-bottom: 20px;
  margin-right: 13px;
}

.categorias {
  color: rgb(59, 59, 59);
  font-size: medium;
}

.biografia {
  height: 300px;
}

.main {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  padding: 30px;
  border: 3px solid white;
  border-radius: 10px;
  background-color: rgba(240, 248, 255, 0.459);
  width: 1000px;
  box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
}

#inputGroupFile01 {
  margin-top: 10px;
}

.btn {
  width: 170px;
  height: 40px;
  border-radius: 10px;
  border: 2px solid white;
  color: rgb(41, 40, 40);
  font-weight: 500;
  background-color: rgba(195, 81, 247, 0.459);
  margin-top: 20px;
  margin-left: 20%;
}

.btn:hover {
  width: 200px;
  height: 50px;
  background-color: rgba(218, 139, 255, 0.459);
}
.informacoes-principais{
  display: flex;
  align-items: center;
  justify-content: center;
}
.nome-email{
  padding: 20px;
}
.informacoes-principais h1{
  display: inline;
  color: #4D4B4B;
}
.informacoes-principais h2{
  font-size: 22px;
  color: #4D4B4B;
  margin-left: 5px;
}
img{
  border-radius: 50%;
}
</style>
