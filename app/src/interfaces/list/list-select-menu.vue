<template>
	<v-menu show-arrow placement="bottom-end">
		<template #activator="{ toggle }">
			<v-icon clickable name="more_vert" @click="toggle" />
		</template>

		<v-list>
			<v-list-item clickable @click="$emit('edit')">
				<v-list-item-icon>
					<v-icon name="edit" />
				</v-list-item-icon>
				<v-list-item-content>
					{{ t('edit') }}
				</v-list-item-content>
			</v-list-item>

			<v-list-item clickable @click="$emit('duplicate')">
				<v-list-item-icon>
					<v-icon name="content_copy" />
				</v-list-item-icon>
				<v-list-item-content>{{ t('duplicate') }}</v-list-item-content>
			</v-list-item>

			<v-divider />

			<v-list-item v-if="delete" clickable class="danger" @click="$emit('delete')">
				<v-list-item-icon>
					<v-icon name="delete" />
				</v-list-item-icon>
				<v-list-item-content>
					{{ t('delete') }}
				</v-list-item-content>
			</v-list-item>
		</v-list>
	</v-menu>
</template>

<script setup lang="ts">
import { useI18n } from 'vue-i18n';
import { defineProps, defineEmits } from 'vue';

defineProps({
  delete: { type: Boolean, default: true },
})

const { t } = useI18n();
const emit = defineEmits(['edit', 'duplicate', 'delete']);
</script>

<style scoped>
.v-list-item.danger {
	--v-list-item-color: var(--danger);
	--v-list-item-color-hover: var(--danger);
	--v-list-item-icon-color: var(--danger);
}
</style>
