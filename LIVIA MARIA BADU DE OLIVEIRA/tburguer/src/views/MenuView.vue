<template>
    <div>
        <h1>Menu</h1>
        <div id= "scroll-horizontal">
            <div id="card-content">
                <div id="card-linha">
                    <div class="foto-hamburguer">
                        <img src="https://guiadacozinha.com.br/wp-content/uploads/2019/11/hamburguer-mexicano.jpg" alt="Imagem do hamburguer">
                        <div class="card-coluna">
                            <p id="nome-content"> Nome Burguer</p>
                            <p id="preco-content">R$ 45,99</p>
                            <p id="descricao-content">Descrição</p>
                            <button>Selecionar</button>
                        </div>

                    </div>
                 </div>
            </div>
            

        </div>
    </div>




</template>
<script>
export default{
    name: "MenuView",
    data() {
        return {
            listaMenuHamburgues: []
        };

    },
    methods: {
        async consultarmenu(){
            const response = await fetch("http://localhost:3000/menu");
            const dados = response.json();
            this.listaMenuHamburgues = dados.burgues;
            console.log(this.listaMenuHamburgues)
        }

    }, 
    mounted() {
        this.consultarmenu();
    }
}
</script>

<style scoped>

#card-content{
    display: inline-block;
    width: 280px;
    min-height: 500px;
    margin: 20px;
    border: 1px solid #ddd;
    border-radius:10px;
    overflow: hidden;
    box-shadow: 0 4px 8px #444;
    position:relative;
}

    #scroll-horizontal{
        flex:1;
        overflow-x: auto;
        white-space: nowrap;
        width:700px ;
        margin: 0 auto;
        box-shadow: inset -10px 0 px 15px -20px grey;
    }

    .foto-hamburguer{
        flex-shrink: 0;
    }
    .foto-hamburguer img{
width: 100%;
max-height: 200px;
object-fit: cover;
border-radius: 10 px 0 0;
    }
    #nome-content{
        font-size: 35px;
        font-weight: bold;
        text-align: center;
        width: 100%;
        
    }
    #preco-content{
        
        font-size: 35px;
        font-weight: bold;
        text-align: center;
        width: 100%;
        color: yellowgreen;
    }

    #descricao-content{
        
        font-size: 16px;
        text-align: left;
        color: gray;
        margin: 16px;
        white-space: pre-line;
        overflow: hidden;
        text-overflow: ellipsis ;
        display: -webkit-box;
        -webkit-line-clamp: 6;
        -webkit-box-orient: 6;/*numeros de linha para cortar*/
        -webkit-box-orient: vertical;
    }
    .card-coluna p{
        margin: 0;


    }
    .card-coluna button{
        margin-top: auto;
        padding:10px ;
        background-color: rgb(149,211,90);
        color: darkslategray;
        font-weight: bold;
        border-radius: 5px;
        border: none;
        font-size: 14px;
        width: 100%;
        transition: 0,5s;
        cursor: pointer;
    }
    .card-coluna button:hover{
       
        background-color: transparent;
        color: darkslategray;
        border: solid 1px rgb(149,211,90);
        font-size: 14px;}
        
        .card-linha{
       
       display: flex;
       flex-direction: row;
       height: 100%;
    }
</style>
