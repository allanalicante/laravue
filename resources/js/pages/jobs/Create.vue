<script setup lang="ts">
import AppLayout from '@/layouts/AppLayout.vue';
import { type BreadcrumbItem } from '@/types';
import { Head } from '@inertiajs/vue3';
import Button from '@/components/ui/button/Button.vue';
import Label from '@/components/ui/label/Label.vue';
import Input from '@/components/ui/input/Input.vue';
import { useForm } from '@inertiajs/vue3';

const breadcrumbs: BreadcrumbItem[] = [
    {
        title: 'Create Job',
        href: '/jobs/create',
    },
];

const form = useForm({
    name: '',
    description: '',
    category: '',
});

const handleSubmit = () => {
    form.post(route('jobs.store'));
}

</script>

<template>
    <Head title="Create Job" />

    <AppLayout :breadcrumbs="breadcrumbs">
        <div class="p-4">
            <form @submit.prevent="handleSubmit" class="space-y-6">
                <div class="space-y-4">
                    <Label for="Job Name">Name</Label>
                    <Input v-model="form.name" type="text" placeholder="Enter Job Name" />
                    <div v-if="form.errors.name" class="text-sm text-red-600">{{ form.errors.name }}</div>
                </div>
                <div class="space-y-4">
                    <Label for="Job Description">Description</Label>
                    <Input v-model="form.description" type="text" placeholder="Enter Job Description" />
                    <div v-if="form.errors.description" class="text-sm text-red-600">{{ form.errors.description }}</div>
                </div>
                <div class="space-y-4">
                    <Label for="Job Category">Category</Label>
                    <Input v-model="form.category" type="text" placeholder="Enter Job Category" />
                    <div v-if="form.errors.category" class="text-sm text-red-600">{{ form.errors.category }}</div>
                </div>
                <Button type="submit">Create Job</Button>
            </form>
        </div>
    </AppLayout>
</template>
