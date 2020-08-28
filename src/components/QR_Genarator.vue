<template>
    <div>
        <div class="qrbox">
            <img src="../assets/default.png" alt="qr-code"><br>
            <textarea v-model="textarea" rows="3"></textarea><br>
            <button @click="generateQR" >Generate QR Code</button>
        </div>
    </div>
</template>

<script>
const baseUrl = "http://api.qrserver.com/v1/create-qr-code/";
export default {
    name:'test',
    data() {
        return {
            textarea:''
        }
    },
    methods:{
        generateQR(){
                let size = "1000x1000";
                let data = this.textarea;
                let qrcode = document.querySelector("img");
                console.log(qrcode);
                console.log("HI==>",data);
                
                let url = `${baseUrl}?data=${data}&size=${size}`;
                qrcode.src =url
            }
    }
}
</script>

<style scoped>
.qrbox{
    width:100%;
    height: 100%;
    text-align: center;

}
button{
    border: none;
    background-color: rgb(9, 145, 9);
    width: 120px;
    height: 30px;
    color: white;
    margin: 10px 0px 0px 0px;
    border-radius: 20px;
    width: 220px;
}
img{
    width: 220px;
    height: 200px;
    border: 1px solid rgb(9, 145, 9);
    outline: none;
}
textarea{
    width: 220px;
    border: 1px solid rgb(9, 145, 9);
    outline: none;
}
</style>