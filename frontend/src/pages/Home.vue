<template>
	<div class="max-w-3xl py-12 mx-auto">
		<!-- <h2 class="font-bold text-lg text-gray-600 mb-4">Welcome {{ session.user }}!</h2>

		<Button
			theme="gray"
			variant="solid"
			icon-left="code"
			@click="ping.fetch"
			:loading="ping.loading"
		>
			Click to send 'ping' request
		</Button>
		<div>
			{{ ping.data }}
		</div>
		<pre>{{ ping }}</pre>

		<div class="flex flex-row space-x-2 mt-4">
			<Button @click="showDialog = true">Open Dialog</Button>
			<Button @click="session.logout.submit()">Logout</Button>
		</div> -->

		<!-- Dialog -->
		<!-- <Dialog title="Title" v-model="showDialog"> Dialog content </Dialog> -->
		<ul>
			<li v-for="action in actions.data" :key="action.index">
				{{ action?.title }}
				-
				{{ action?.status }}
				
			</li>
		</ul>
	</div>
</template>

<script setup>
import { ref } from 'vue'
import { Dialog, createListResource } from 'frappe-ui'
import { createResource } from 'frappe-ui'
import { session } from '../data/session'

const ping = createResource({
	url: 'ping',
	auto: true,
})

const actions = createListResource({
	doctype: 'Action',
	fields: ['title', 'status', 'description', 'date', 'due_date'],
	limit: 100,
})

actions.reload()
console.log(actions)

const showDialog = ref(false)
</script>
