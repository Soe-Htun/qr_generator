<template>
    <div>
        <div class="qrbox">
            <img src="../assets/default.png" alt="qr-code"><br>
            <textarea v-model="textarea" rows="3"></textarea><br>
            <button @click="generateQR" >Generate QR Code</button>
        </div>
        <button @click="get()">Get Screenshot</button>
    </div>
</template>

<script>
import html2canvas from 'html2canvas'
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
            //let size = "1000x1000";
            let data = this.textarea;
            let qrcode = document.querySelector("img");
            console.log(qrcode);
            console.log("HI==>",data);
            
            let url = `${baseUrl}?data=${data}`;
            qrcode.src =url
        },
        get(){
            //take screenshot and download this image
            html2canvas(document.querySelector(".qrbox")).then(canvas => {
                document.body.appendChild(canvas)
                }).then(() => {
                    var canvas = document.querySelector('canvas');
                    canvas.style.display = 'none';
                    var image = canvas.toDataURL("image/png").replace("image/png", "image/octet-stream");
                    var a = document.createElement("a");
                    a.setAttribute('download', 'myImage.png');
                    a.setAttribute('href', image);
                    a.click();
            })
        },
        onCLick(e){
            if(e.keyCode === 13){
                this.generateQR()
            }
        }
    },
    created(){
        window.addEventListener("keydown", this.onCLick)
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
    width: 200px;
    height: 180px;
    padding: 10px;
    border: 1px solid rgb(9, 145, 9);
    outline: none;
}
textarea{
    width: 220px;
    border: 1px solid rgb(9, 145, 9);
    outline: none;
}
</style>