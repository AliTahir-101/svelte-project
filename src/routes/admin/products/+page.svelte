<script lang="ts">
	import { Button } from '$lib/components/ui/button';
	import { Input } from '$lib/components/ui/input';
	import * as Table from '$lib/components/ui/table';

	let showProduct = $state(false);
</script>

<div class="space-y-4 p-8 pt-6">
	<div class="items-center justify-center space-y-2">
		<h2 class="text-3xl font-bold tracking-tight capitalize">Products</h2>
		<div class="flex items-center space-x-2">
			<Input placeholder="Search products..." class="w-[150px] lg:w-[250px]" />
			<Button href="/products/add">Add Product</Button>
		</div>
	</div>
	{#if showProduct}
		<Table.Root>
			<Table.Header>
				<Table.Row>
					<Table.Head class="w-[100px]">ID</Table.Head>
					<Table.Head>Image</Table.Head>
					<Table.Head>Name</Table.Head>
					<Table.Head>Category</Table.Head>
					<Table.Head>Sub Category</Table.Head>
					<Table.Head>Price</Table.Head>
					<Table.Head>Stock</Table.Head>
					<Table.Head class="text-right">Actions</Table.Head>
				</Table.Row>
			</Table.Header>
			<Table.Body>
				<Table.Row>
					<Table.Cell class="font-medium">1</Table.Cell>
					<Table.Cell>
						<img src="https://picsum.photos/30" alt="Product Image" />
					</Table.Cell>
					<Table.Cell>Product Name</Table.Cell>
					<Table.Cell>Category Name</Table.Cell>
					<Table.Cell>Sub Category Name</Table.Cell>
					<Table.Cell>$100.00</Table.Cell>
					<Table.Cell>In Stock</Table.Cell>
					<Table.Cell class="text-right">
						<Button variant={'destructive'}>Delete</Button>
					</Table.Cell>
				</Table.Row>
			</Table.Body>
		</Table.Root>
	{:else}
		<p
			class="text-muted-foreground flex h-[70vh] w-full flex-col items-center justify-center gap-3 text-center text-3xl"
		>
			<span class="text-muted-foreground">No products found</span>
			<span class="text-muted-foreground">Please add a product to get started.</span>
			<Button href="/products/add" >Add Product</Button>
		</p>
	{/if}
</div>
