<script setup>
import { ref, reactive, computed } from "vue";
const enviado = ref(false);

const usuario = reactive({
  nome: "",
  sobrenome: "",
  nascimento: "",
  senha: "",
  confirmacaoSenha: "",
  cep: "",
  estado: "",
  cidade: "",
  biografia: "",
  hobbies: [],
  linguagem: "",
  avatar: "",
});

const validacao = computed(() =>
  usuario.senha == usuario.confirmacaoSenha ? "" : "senha-invalida"
);

function enviar() {
  if (usuario.senha === usuario.confirmacaoSenha) {
    enviado.value = true;
  }
}

const estados = [
  { sigla: "AC", nomeEstado: "Acre" },
  { sigla: "AL", nomeEstado: "Alagoas" },
  { sigla: "AP", nomeEstado: "Amapá" },
  { sigla: "AM", nomeEstado: "Amazonas" },
  { sigla: "BA", nomeEstado: "Bahia" },
  { sigla: "CE", nomeEstado: "Ceará" },
  { sigla: "DF", nomeEstado: "Distrito Federal" },
  { sigla: "ES", nomeEstado: "Espírito Santo" },
  { sigla: "GO", nomeEstado: "Goiás" },
  { sigla: "MA", nomeEstado: "Maranhão" },
  { sigla: "MT", nomeEstado: "Mato Grosso" },
  { sigla: "MS", nomeEstado: "Mato Grosso do Sul" },
  { sigla: "MG", nomeEstado: "Minas Gerais" },
  { sigla: "PA", nomeEstado: "Pará" },
  { sigla: "PB", nomeEstado: "Paraíba" },
  { sigla: "PR", nomeEstado: "Paraná" },
  { sigla: "PE", nomeEstado: "Pernambuco" },
  { sigla: "PI", nomeEstado: "Piauí" },
  { sigla: "RJ", nomeEstado: "Rio de Janeiro" },
  { sigla: "RN", nomeEstado: "Rio Grande do Norte" },
  { sigla: "RS", nomeEstado: "Rio Grande do Sul" },
  { sigla: "RO", nomeEstado: "Rondônia" },
  { sigla: "RR", nomeEstado: "Roraima" },
  { sigla: "SC", nomeEstado: "Santa Catarina" },
  { sigla: "SP", nomeEstado: "São Paulo" },
  { sigla: "SE", nomeEstado: "Sergipe" },
  { sigla: "TO", nomeEstado: "Tocantins" },
];

function handleFileUpload(e) {
  const target = e.target;
  console.log(target);
  if (target && target.files) {
    const file = target.files[0];
    usuario.avatar = URL.createObjectURL(file);
  }
}
</script>

<template>
  <main>
    <div class="perfil-usuario" v-if="enviado">
      <section class="informacoes-principais">
        <img v-if="usuario.avatar" class="avatar" :src="usuario.avatar" />
        <div class="nome-email">
          <h1>{{ usuario.nome }}</h1>
          <h2>{{ usuario.sobrenome }}</h2>
          <div class="usuario-email">
            <h3>{{ usuario.email }}</h3>
          </div>
        </div>
      </section>
      <div class="informacoes-usuario">
        <section class="container endereco">
          <span>Cep: {{ usuario.cep }}</span>
          <span>Cidade: {{ usuario.cidade }}</span>
          <span>Estado: {{ usuario.estado }}</span>
        </section>
      </div>
      <div class="container-biografia-preferidos">
        <section class="container biografia">
          <h1>Biografia</h1>
          <span>{{ usuario.biografia }}</span>
        </section>
        <section class="container preferidos">
          <div>
            <span>Linguagem preferida: {{ usuario.linguagem }}</span>
          </div>
          <div>
            <span>Hobbies:</span>
            <span class="hobbies">{{ usuario.hobbies }}</span>
          </div>
        </section>
      </div>
    </div>
    <div class="perfil" v-else>
      <img src="../src/perfil (2).png" width="40px" />
      <h1>Perfil</h1>
      <form @submit.prevent="enviar()" class="row g-4" validation>
        <div class="col-md-5">
          <input
            v-model="usuario.nome"
            type="text"
            class="form-control"
            id="inputEmail4"
            placeholder="nome"
            required
          />
        </div>
        <div class="col-md-5">
          <input
            v-model="usuario.sobrenome"
            type="text"
            class="form-control"
            id="inputPassword4"
            placeholder="sobrenome"
            required
          />
        </div>
        <div class="col-md-2">
          <input
            v-model="usuario.nascimento"
            type="date"
            class="form-control"
            id="inputPassword4"
            placeholder="nascimento"
            required
          />
        </div>
        <div class="col-4">
          <input
            v-model="usuario.email"
            type="email"
            class="form-control"
            id="inputEmail4"
            placeholder="email"
            required
          />
        </div>
        <div class="col-md-4">
          <input
            v-model="usuario.senha"
            type="password"
            class="form-control"
            id="inputPassword4"
            placeholder="insira sua senha"
            required
          />
        </div>
        <div class="col-md-4">
          <input
            v-model="usuario.confirmacaoSenha"
            type="password"
            class="form-control"
            :class="validacao"
            id="inputPassword4"
            placeholder=" confirme sua senha"
            required
          />
          <div v-if="usuario.senha != usuario.confirmacaoSenha" style="color: red">
            senha incorreta
          </div>
        </div>
        <div class="col-md-2">
          <input
            v-model="usuario.cep"
            type="number"
            class="form-control"
            id="inputZip"
            placeholder="CEP"
            required
          />
        </div>
        <div class="col-md-4">
          <select
            v-model="usuario.estado"
            id="inputState"
            class="form-select"
            placeholder="estado"
            required
          >
            <option selected disabled>Estado</option>
            <option v-for="opcao in estados" :key="opcao" :value="opcao.nomeEstado">
              {{ opcao.sigla }}
            </option>
          </select>
        </div>
        <div class="col-md-6">
          <input
            v-model="usuario.cidade"
            type="text"
            class="form-control"
            id="inputCity"
            placeholder="cidade"
            required
          />
        </div>

        <div class="col-4">
          <textarea
            v-model="usuario.biografia"
            cols="35"
            rows="6"
            placeholder="Biografia"
            class="form-control"
            required
          />
        </div>
        <div class="col-2">
          <h1 class="categorias">Hobbies:</h1>
          <div class="form-check">
            <input
              v-model="usuario.hobbies"
              class="form-check-input"
              type="checkbox"
              name="esportes"
              value="Esportes"
            />
            <label class="form-check-label" for="esportes"> Esportes </label>
          </div>
          <div class="form-check">
            <input
              v-model="usuario.hobbies"
              class="form-check-input"
              type="checkbox"
              name="ler"
              value="Ler"
            />
            <label class="form-check-label" for="ler"> Ler </label>
          </div>
          <div class="form-check">
            <input
              v-model="usuario.hobbies"
              class="form-check-input"
              type="checkbox"
              name="cozinhar"
              value="Cozinhar"
            />
            <label class="form-check-label" for="cozinhar"> Cozinhar </label>
          </div>
          <div class="form-check form-check-inline">
            <input
              v-model="usuario.hobbies"
              class="form-check-input"
              type="checkbox"
              name="games"
              value="Games"
            />
            <label class="form-check-label" for="games"> Games </label>
          </div>
        </div>
        <div class="col-2">
          <h1 class="categorias">Best language:</h1>
          <div class="form-check">
            <input
              v-model="usuario.linguagem"
              class="form-check-input"
              type="radio"
              name="language"
              value="Python"
            />
            <label class="form-check-label" for="language"> Python </label>
          </div>
          <div class="form-check">
            <input
              v-model="usuario.linguagem"
              class="form-check-input"
              type="radio"
              name="language"
              value="PHP"
            />
            <label class="form-check-label" for="language"> PHP </label>
          </div>
          <div class="form-check">
            <input
              v-model="usuario.linguagem"
              class="form-check-input"
              type="radio"
              name="language"
              value="Java"
            />
            <label class="form-check-label" for="language"> Java </label>
          </div>
          <div class="form-check form-check-inline">
            <input
              v-model="usuario.linguagem"
              class="form-check-input"
              type="radio"
              name="language"
              value="Javascript"
            />
            <label class="form-check-label" for="language"> Javascript </label>
          </div>
        </div>
        <div class="col-4">
          <div class="form-check">
            <label class="form-check-label" for="inputFile">Foto de perfil:</label>
            <input
              type="file"
              class="form-control"
              id="inputFile"
              @change="handleFileUpload($event)"
              required
            />
            <input type="submit" class="btn btn-primary" value="Enviar" />
          </div>
        </div>
      </form>
    </div>
  </main>
</template>
"
<style scoped>
.senha-invalida {
  border: 1px solid red;
}
.informacoes-usuario {
  display: flex;
  align-items: center;
  justify-content: center;
}
.perfil h1 {
  color: white;
  display: inline;
}

img {
  width: 50px;
  margin-bottom: 20px;
  margin-right: 13px;
}

.categorias {
  color: rgb(59, 59, 59);
  font-size: medium;
}

main {
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

#inputFile {
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
.informacoes-principais {
  display: flex;
  align-items: center;
  justify-content: center;
}
.nome-email {
  padding: 20px;
}
.usuario-email {
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 10px;
}
.informacoes-principais h1 {
  display: inline;
  color: #4d4b4b;
  font-size: 25px;
}
.informacoes-principais h2 {
  display: inline;
  font-size: 25px;
  color: #4d4b4b;
  margin-left: 10px;
}
.informacoes-principais h3 {
  display: inline;
  font-size: 18px;
  color: #4d4b4b;
}
.informacoes-principais img {
  width: 90px;
  border-radius: 50%;
  border: 3px solid #4d4b4b;
  margin-bottom: 20px;
  margin-right: 13px;
  border-radius: 50%;
}
.container-biografia-preferidos {
  display: flex;
  align-items: center;
  justify-content: center;
}
.container {
  border-radius: 15px;
  border: 2px solid #ffffff;
  margin: 25px;
  background-color: #6b0d9725;
  padding: 10px;
  width: max-content;
}
.endereco {
  background-color: #6b0d9725;
  padding: 10px;
  width: max-content;
}
.endereco span {
  color: white;
  font-size: 18px;
  margin: 50px;
}
span {
  color: white;
  font-size: 18px;
}
.hobbies {
  display: block;
}
.biografia h1 {
  font-size: 25px;
  color: white;
}
.preferidos {
  padding: 25px;
  width: 40%;
  min-height: 220px;
}
.biografia {
  padding: 25px;
  width: 50%;
  min-height: 220px;
}
</style>
