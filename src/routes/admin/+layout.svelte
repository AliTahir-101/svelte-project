<script lang="ts">
	import * as Sidebar from '$lib/components/ui/sidebar/index.js';
	import SidebarProvider from '$lib/components/ui/sidebar/sidebar-provider.svelte';
	import { Blocks, Box, Home, LayoutDashboard, Truck, User } from 'lucide-svelte';

	let { children } = $props();
	// Menu items.
	const items = [
		{
			title: 'Overview',
			url: 'overview',
			icon: LayoutDashboard
		},
		{
			title: 'Products',
			url: 'products',
			icon: Box
		},
		{
			title: 'Users',
			url: 'users',
			icon: User
		},
		{
			title: 'Orders',
			url: 'orders',
			icon: Truck
		},
		{
			title: 'Categories',
			url: 'categories',
			icon: Blocks
		},
		{
			title: 'Store Front',
			url: '../',
			icon: Home
		}
	];
</script>

<SidebarProvider>
	<Sidebar.Root>
		<Sidebar.Content>
			<Sidebar.Group>
				<Sidebar.GroupLabel>Admin Dashboard</Sidebar.GroupLabel>
				<Sidebar.GroupContent>
					<Sidebar.Menu>
						{#each items as item (item.title)}
							<Sidebar.MenuItem>
								<Sidebar.MenuButton>
									{#snippet child({ props })}
										<a href={`/admin/${item.url}`} {...props}>
											<item.icon />
											<span>{item.title}</span>
										</a>
									{/snippet}
								</Sidebar.MenuButton>
							</Sidebar.MenuItem>
						{/each}
					</Sidebar.Menu>
				</Sidebar.GroupContent>
			</Sidebar.Group>
		</Sidebar.Content>
	</Sidebar.Root>
	<main class="flex-1">
		<Sidebar.Trigger />
        {@render children?.()}
	</main>
</SidebarProvider>
