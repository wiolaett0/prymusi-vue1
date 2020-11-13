<template>
	<div id="container-fluid">
		<nav class="navbar navbar-light bg-light">
			<span class="navbar-text">Participants list</span>
		</nav>
		<div class="participant-list">
		<h1>Participants</h1>
		<div v-if="participants.length> 0">
			<div v-for="participant in participants" v-bind:key="participamt">
			{{participant.name}}  {{participant.surname}} 
			<button v-on:click="onRemove(participant)" type="button" class="btn btn danger">Remove</button>
			</div>
			</div>
		<div v-else class="alert alert-light" role="alert> Ooops. Nothing here ;C</div>
		</div>
		<h1>List</h1>
		<div v-if="participants.length > 0">
			<div v-for="participant in participants" :key="participant.name">{{ participant.name}} {{ participant.lastName}} </div>
		</div>
		<div v-else class="alert alert-dark" role="alert">No participants yet!</div>
		<form>
				<h1>Add Participant</h1>
				<div class="form-group">
			<label for="participant-name">Name</label>
		<input class="form-control" id="participant-name" placeholder="Enter name" v-model="newParticipantName">
					</div>
		<div class="form-group">
			<label for="participant-last-name">Last name</label>
			<input class="form-control" id="participant-last-name" placeholder="Enter last name" v-model="newParticipantLastName">
		</div>
			<button type="submit" class="btn btn-primary" v-on:click.prevent="addParticipant()">Submit</button>
		</form>
	</div></div>
  
</template>

<script>
	export default {
	 data: function (){
		 return {
		 participants: [],
		 newParticipantName: null,
		 newParticipantLastName: null,
		 }
		 },
	methods: {

		addParticipant: function(){
		 var newParticipant = { name: this.newParticipantName, lastName: this.newParticipantLastName };
		 newParticipant.id = Math.random();
		 this.participants.push(newParticipant);
		 this.newParticipantName = null;
		this.newParticipantLastName = null;
	 },
	 onRemove: function (participant){
		this.participants = this.participants.filter((p) => { return p.id !== participant.id});
	 }
		 }//
		}
</script>

<style>
	.container-fluid {
	padding: 0;
	margin: 0;
	}
</style>


