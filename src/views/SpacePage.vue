<template>
		
	<RightSideСalendar />
</template>

<script>
import RightSideСalendar from '../components/RightSideСalendar.vue';
import { mapGetters } from "vuex";

export default {
	components: {
		RightSideСalendar
	},
	data(){
		return {
			dialog: false,
			dialogInformation: false,
			information: "",
			dialogData: {
				name: null,
				faces: [],
				comment: null,
				backcol: [
					"", "", "", "", "", "", "", ""
				]
			}
		}
	},
	computed: {
		...mapGetters(["getPeoples", "getSpace"]),
	},
	watch: {
		dialog: {
			handler(){
				if (!this.dialog){
					this.dialogData = {
						name: null,
						faces: [],
						comment: null,
						backcol: [
							"", "", "", "", "", "", "", ""
						]
					};
				}
			}
		}
	},
	methods: {
		changeBaccol(N) {
			if (this.dialogData.backcol[N] == "") { 
				this.dialogData.backcol[N] = "background-color: #C0C0C0;"; 
			}
			else { 
				this.dialogData.backcol[N] = ""; 
			}
		},
		addEl(newEl) {
			if (this.dialogData.faces.length < 2) {
				this.dialogData.faces.push(newEl);
			}
		},
		check() {
			if (this.dialogData.faces.length == 2) {
				alert("Ошибка! Может быть только 2 исполнителя.");
			}
		},
		deleteEl(delEl) {
			this.dialogData.faces.splice(delEl, 1);
		},
		sendInvitation() {
			alert("Приглашение отправлено!");
			this.dialog = false;
		},
		openInfo(info) {
			this.information = info;
			this.dialogInformation = true;
		},
	}
}
</script>

<style name="page" scoped>
	.page {
		margin-top: 4.5%;
		color: azure;
		margin-left: 3.4%;
		width: 70%;
	}
	.component{
		display: flex;
		flex-direction: column;
		justify-content: space-between;
		flex-basis: 10%;
		background-color: #F0F0F0;
		color: #000000;
		border-radius: 5px;
		margin: 0 3.5%;
		margin-bottom: 4%;
	}
	.component > .header{
		display: flex;
		flex-basis: 15%;
		margin: 0.5%;
		margin-bottom: 7%;
	}
	.component > .footer{
		display: flex;
		flex-direction: column;
		flex-basis: 45%;
		border-radius: 5px;
		margin: 0.8%;
	}
	.component > .header > .button{
		font-size: 10px;
		font-weight: bold;
		margin: 0.5%;
	}
	.component > .footer > .header{
		display: flex;
		flex-basis: 20%;
		margin: 1.3% 0;
		user-select: none;
	}
	.component > .footer > .main{
		display: flex;
		flex-basis: 80%;
		background-color: #E6EBF2;
	}
	.component > .footer > .main > .times{
		display: flex;
		flex-direction: column;
		justify-content: center;
		/* align-items: center; */
		flex-basis: 75%;
	}
	.component > .footer > .main > .actions{
		display: flex;
		flex-direction: column;
		justify-content: center;
		flex-basis: 25%;
	}
	.component > .footer > .main > .times > .times_row{
		display: flex;
		margin: 5px 0;
	}
	.component > .footer > .main > .actions > .button{
		font-size: 10px;
		font-weight: bold;
		margin: 5px;
	}
	.component > .footer > .main > .times > .times_row > .time{
		display: flex;
		font-size: 12px;
		margin-right: 10px;
		padding: 4px 15px;
		border: 2px solid #CFD8E5;
		border-radius: 5px;
		user-select: none;
	}
</style>

<style name="dialog" scoped>
	.infoDial {
		text-align: center;
		background-color: #ececec;
		width: 400px;
		padding: 20px;
		border-radius: 10px;
	}
	.forbd {
		margin-top: 15px;
		display: flex;
		justify-content: center;
		align-items: center;
	}
	.forp {
		border-radius: 10px;
		background-color: #C0C0C0;
		padding: 6px;
	}
	.faces-container {
		height: 50px;
		display: flex;
		align-items: center;
	}
	.ftime {
		width: 150px;
		margin-right: 10px;
		margin-bottom: 10px;
		border-radius: 10px;
	}
	.fdial {
		background-color: #ececec;
		width: 520px;
		padding: 20px;
		border-radius: 10px;
	}
</style>

<style name="custom" scoped>
	.active_time{
		background-color: #ABBAD0;
	}
</style>