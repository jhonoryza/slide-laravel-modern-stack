---
theme: seriph
background: https://cover.sli.dev
title: Presentation - Fajar
class: text-center
drawings:
  persist: false
transition: slide-left
mdc: true
---

# Building Full-Stack Apps with a Backend-Driven Approach

---
layout: image-right
image: /kit.png
backgroundSize: cover
---

# Case: Laravel Framework

A quick look at the tools that shape modern Laravel development.

- [Livewire](https://laravel.com/docs/12.x/starter-kits#livewire)
- [Inertia React](https://laravel.com/docs/12.x/starter-kits#react)
- [Inertia Vue](https://laravel.com/docs/12.x/starter-kits#vue)

---
layout: split
---

::left::

<div v-click class="transition-all duration-500">

# Livewire

[Livewire](https://livewire.laravel.com) is a package for Laravel that allows
you to build dynamic interfaces using PHP, similar to
[Ruby's Hotwire](https://hotwired.dev).

![livewire](./public/livewire.png)

</div>

::right::

<div v-click class="transition-all duration-500">

## **How it works:**

You write PHP classes (called components) that render Blade templates. User
interactions trigger AJAX requests back to the server, which re-renders the
component and sends the updated HTML back to the client.

- Return HTML from AJAX requests
- Doesn't replace javascript, but abstracts the javascript
- No new syntax, Using blade templating and has new directive (wire:model or
  wire:click)
- Distinct separation server code (livewire) and client code (javascript or
  [alpinejs](https://alpinejs.dev))

</div>

---
layout: full
---

# Declarative Approach

<div v-click class="transition-all duration-500">

## Flutter

<div class="flex items-center gap-4">
    <img src="https://juststickers.in/wp-content/uploads/2019/01/flutter.png"
        class="w-12"
    />
    <img src="https://www.nicepng.com/png/detail/259-2592669_ios-android-icon-png-clip-art-free-ios.png"
        class="w-12"
    />
</div>

</div>

<div v-click class="transition-all duration-500">

```dart
children: [
    Column(
    mainAxisAlignment: MainAxisAlignment.start,
    crossAxisAlignment: CrossAxisAlignment.start,
    children: [
        Container(height: 80),
        Text(
            'Hello World',
            textAlign: TextAlign.center,
            style: TextStyle(
                fontSize: 24,
                fontWeight: FontWeight.bold,
                color: Colors.white,
                fontFamily: GoogleFonts.quicksand().fontFamily,
            ),
        ),
    ...
```

</div>

---
layout: split
---

::left::

# Declarative Approach

<div v-click class="transition-all duration-500">

## Swiftui

<div class="flex items-center gap-4">
    <img src="/swiftui.jpg"
        class="w-12"
    />
</div>

</div>

<div v-click class="transition-all duration-500">

<div class="flex items-center gap-4">
    <img src="/swiftui2.png" />
</div>

</div>

::right::

<div v-click class="transition-all duration-500">

```swift
var body: some View {
        VStack(spacing: 0) {
            // Toolbar
            HStack {
                Text(settings.lastOpenedFileURL?.lastPathComponent ?? "Untitled")
                    .font(.title2)
                    .fontWeight(.semibold)
                
                Spacer()
                
                Button("Save") {
                    showSavePanel()
                }
                .keyboardShortcut("s", modifiers: [.command, .shift])

                Button("Open") {
                    showOpenPanel()
                }
                .keyboardShortcut("o", modifiers: .command)

                Button(action: runCode) {
                    HStack(spacing: 4) {
                        Image(systemName: "play.fill")
                        Text("Run Code")
                    }
                }
```

</div>
---
layout: split
---

::left::

# FilamentPHP

<div v-click class="transition-all duration-500">

- [Filament](https://filamentphp.com) is a Server-Driven UI framework for
  Laravel.
- Define UI entirely in PHP using structured objects.
- Built on Livewire, Alpine.js, Tailwind CSS.

![Filament Logo](/filament.png)

</div>

<div v-click class="transition-all duration-500">

### What is Server-Driven UI?

- SDUI is a proven architecture used by Meta, Airbnb, Shopify.
- Server controls UI, allows faster iteration & centralized logic.

</div>

::right::

<div v-click class="transition-all duration-500">

# Why it was created?

- To rapidly build beautiful admin panels and forms.
- Provides a pre-built architecture for common application UIs.

</div>

<div v-click class="transition-all duration-500">

# The Approach

It follows a **backend-driven** or **declarative** approach.

1. You define the entire structure of your UI (forms, fields, table columns,
   actions) in PHP classes.
2. Filament then takes care of rendering the corresponding Blade and Livewire
   components on the frontend.
3. You build complex interfaces without touching frontend code.

</div>

---
layout: split
---

::left::

# Example

<div v-click class="transition-all duration-500">

the form builder code generate this form UI

![ehh](./public/ehh.png)

</div>

::right::

# Form Builder

<div v-click class="transition-all duration-500">

declarative syntax

```php
Tab::make('Indonesia')
->schema([
    TextInput::make('title.id')
        ->label('Title')
        ->lazy()
        ->afterStateUpdated(
            function ($set, $state) {
                $set('slug.id', Str::slug($state));
            }
        )
        ->required(),
    TextInput::make('slug.id')
        ->label('Slug')
        ->required(),
    Textarea::make('description.id')
        ->label('Description')
        ->rows(3),
    RichEditor::make('content.id')
        ->label('Content')
        ->required()
        ->maxLength(65535),
])
```

</div>

---
layout: split
---

::left::

# Example

<div v-click class="transition-all duration-500">

the table builder code generate this table UI

![table builder](./public/ehh1.png)

![table builder](./public/ehh2.png)

</div>

::right::

# Table Builder

<div v-click class="transition-all duration-500">

declarative syntax

```php
->columns([
    TextColumn::make('title')
        ->searchable(),
    IconColumn::make('is_published')
        ->label('Published')
        ->boolean(),
    TextColumn::make('published_at')
        ->dateTime()
        ->sortable()
        ->toggleable(isToggledHiddenByDefault: false),
])
->filters([
    SelectFilter::make('is_published')
        ->options([
            true => 'Yes',
            false => 'No',
        ])
])
->actions([EditAction::make()])
->bulkActions([
    BulkActionGroup::make([
        DeleteBulkAction::make(),
    ]),
]);
```

</div>

---
layout: image
image: /filament3.png
backgroundSize: contain
---

---
layout: table-layout
columns: 8
---

::title::
Community
::left::
<th>Package</th>
<th>Backend driven</th>
<th>Declarative</th>
<th>Form Builder</th>
<th>Table Builder</th>
<th>CRUD Generator</th>
<th>UI Component</th>
<th>Free / Paid</th>
::body::
<tr>
  <td>Backpack</td>
  <td>✅</td>
  <td>✅</td>
  <td>✅</td>
  <td>✅ (basic)</td>
  <td>✅</td>
  <td>❌ (terbatas)</td>
  <td>Paid</td>
</tr>
<tr>
  <td>FilamentPHP</td>
  <td>✅</td>
  <td>✅</td>
  <td>✅</td>
  <td>✅</td>
  <td>✅</td>
  <td>✅</td>
  <td>Free (MIT)</td>
</tr>
<tr>
  <td>WireUI</td>
  <td>❌</td>
  <td>❌</td>
  <td>❌</td>
  <td>❌</td>
  <td>❌</td>
  <td>✅</td>
  <td>Free (MIT)</td>
</tr>
<tr>
  <td>TallStackUI</td>
  <td>❌</td>
  <td>❌</td>
  <td>❌</td>
  <td>❌</td>
  <td>❌</td>
  <td>✅</td>
  <td>Free</td>
</tr>

---
layout: split
---

::left::

# Inertia

<div v-click class="transition-all duration-500">

[Inertia](https://inertiajs.com) is a new approach to building classic
server-driven web apps. We call it the modern monolith. A tool that connects a
server-side framework (like Laravel) to a client-side framework (like React,
Vue, or Svelte) without the complexity of building a full API.

![inertia](./public/inertia.png)

</div>

::right::

# How it works

<div v-click class="transition-all duration-500">

You build standard Laravel controllers that return Inertia responses. These
responses include the page component name and its data (props). Inertia then
dynamically loads the correct frontend component without a full page reload.

**Use Case:**

Perfect for building modern Single-Page Applications (SPAs) with the power of a
client-side framework, but with the routing and data management handled by
server side framework (like Laravel).

```php
public function show(Permission $permission): Response
{
    return Inertia::render('permissions/show', [
        'permission' => $permission,
        'routeName' => 'permissions',
        'routeId' => $permission->id,
    ]);
}
```

</div>

---
layout: image-right
image: /kit.png
backgroundSize: cover
---

# Laravel starter kit.

- [Inertia React](https://laravel.com/docs/12.x/starter-kits#react)
- [Inertia Vue](https://laravel.com/docs/12.x/starter-kits#vue)

![starter kit](./public/kit1.png)

---
layout: split
---

::left::
<div v-click class="transition-all duration-500">
    <h2>Style</h2>
    <ul>
        <li><a target="_blank" href="https://tailwindcss.com">https://tailwindcss.com</a></li>
    </ul>
</div>

::right::
<div v-click class="transition-all duration-500">
    <h2>UI Components</h2>
    <ul>
        <li><a target="_blank" href="https://ui.shadcn.com">https://ui.shadcn.com</a></li>
    </ul>
</div>

<div v-click class="transition-all duration-500">
    <h2>Shadcn Theme</h2>
    <ul>
        <li><a target="_blank" href="https://tweakcn.com/editor/theme">https://tweakcn.com/editor/theme</a></li>
        <li><a target="_blank" href="https://shadcnstudio.com/theme-generator">https://shadcnstudio.com/theme-generator</a></li>
        <li><a target="_blank" href="https://ui.jln.dev">https://ui.jln.dev</a></li>
        <li><a target="_blank" href="https://tailscan.com/colors">https://tailscan.com/colors</a></li>
    </ul>
</div>

---
layout: table-layout
columns: 8
---

::title::
Community

::left::
<th>Nama</th>
<th>Support</th>
<th>Backend driven</th>
<th>Declarative</th>
<th>CRUD Generator</th>
<th>Form Builder</th>
<th>Table Builder</th>
<th>UI Component</th>
<th>Free / Paid</th>
::body::
<tr>
  <td><strong>Laravel Nova</strong></td>
  <td>Vue</td>
  <td>✅</td>
  <td>✅</td>
  <td>✅</td>
  <td>✅</td>
  <td>✅</td>
  <td>✅</td>
  <td><strong>Paid</strong></td>
</tr>
<tr>
  <td><strong>InertiaUI</strong></td>
  <td>React/Vue</td>
  <td>✅</td>
  <td>✅</td>
  <td>❌</td>
  <td>❌</td>
  <td>✅</td>
  <td>✅ (sedikit)</td>
  <td><strong>Paid</strong></td>
</tr>
<tr>
  <td><strong>Craftable PRO</strong></td>
  <td>Vue</td>
  <td>❌</td>
  <td>✅ (semi)</td>
  <td>✅</td>
  <td>❌</td>
  <td>❌</td>
  <td>❌</td>
  <td><strong>Paid</strong></td>
</tr>
<tr v-click class="transition-all duration-500">
  <td><strong>Inertia Builder</strong></td>
  <td>React/Vue</td>
  <td>✅</td>
  <td>✅</td>
  <td>✅</td>
  <td>✅</td>
  <td>✅</td>
  <td>✅</td>
  <td><strong>Free</strong></td>
</tr>

---
layout: split
---

::left::
<div v-click class="transition-all duration-500">

# Inertia Builder

A package to build inertia react/vue/svelte ui with backend driven approach.

Directly inspired by FilamentPHP's powerful and efficient backend-driven
approach.

- **Declarative UI Construction:** Define forms and data tables in your Laravel
  controllers.
- **Rich Form Fields:** A wide variety of form fields available out-of-the-box.
- **Powerful Data Tables:** Create complex data tables with searching,
  filtering, sorting, and actions.
- **Reactive Components:** Create dependent dropdowns and other reactive form
  elements.
- **Relationship Handling:** Automatically populate fields and table columns
  from Eloquent relationships.
- **Customizable:** Extend the library with your own custom fields and filters.
</div>

::right::

<div v-click class="transition-all duration-500">

# Core Concept: Backend-Driven UI

The structure of the UI (e.g., form fields, table columns) is defined in PHP
controller classes, and a generic set of React components renders the final UI.

# Requirement

- PHP >= 8.4
- Laravel >= 12
- Nodejs & npm >= 20
- Tailwind 4
- Laravel
  [laravel starter kit](https://laravel.com/docs/12.x/starter-kits)
</div>

---
layout: split
---

::left::

# Table Builder

<div v-click class="transition-all duration-500">

Define your entire data table in the `index` method of your controller.

![table](./public/builder.png)

</div>

::right::

<div v-click class="transition-all duration-500">

```php
Table::make(Post::class)
    ->columns([
        TableColumn::make('title')
            ->searchable(),
        TableColumn::make('author.name')
            ->label('Author')
            ->sortable(),
        TableColumn::make('published')
            ->renderUsing(fn ($state) => $state ? 'Yes' : 'No'),
    ])
    ->filters([
        Filter::select('author.name')
            ->label('Author')
            ->relationship(User::class, 'name', 'name'),
        Filter::date('published_at'),
    ])
    ->defaultSort('id', 'desc')
    ->actions([
        Action::make('new')
            ->needRowSelected(false),
        Action::make('delete')
            ->message('Delete this post?'),
    ]);
```

</div>

---
layout: split
---

::left::

# Form Builder

<div v-click class="transition-all duration-500">

Define the fields for your create/edit forms in a reusable private method.

![table](./public/builder1.png)

</div>

::right::

<div v-click class="transition-all duration-500">

```php
Form::make()
    ->model($category)
    ->schema([
        Field::text('name')
            ->state(fn ($state) => ucwords($state))
            ->reactive()
            ->afterStateUpdated(function ($state, Set $set) {
                $set('slug', Str::slug($state));
            }),
        Field::text('slug'),
            ->hidden(function (Get $get) {
                return $get('name') == 'Aa';
            }),
        Field::flatpickr('published_at'),
    ]);
```

</div>

---
layout: split
---

::left::

<div v-click class="transition-all duration-500">

# Dependent Dropdowns Example

Here is how to set up a dependent dropdown for `City` based on the selected
`Province`.

![depend](./public/depend.png)

</div>

::right::

<div v-click class="transition-all duration-500">

```php
Field::select('province_id')
    ->label('Province')
    ->relationship(Province::class, 'name')
    ->reactive(),

Field::select('city_id')
    ->label('City')
    ->placeholder('Select Province first')
    ->relationship(
        modelClass: City::class,
        titleAttr: 'name',
        modifyQueryUsing: function ($query, $get) {
            $provinceId = $get('province_id');
            $query->where('province_id', $provinceId);
        }),
```

</div>

---
layout: split
---

::left::

# Getting Started

<div v-click class="transition-all duration-500">

## 1. Install Package

<a target="_blank" href="https://github.com/jhonoryza/laravel-inertia-builder">Github</a>

```bash
composer require jhonoryza/laravel-inertia-builder
php artisan inertia-builder:install
```

</div>

::right::

<div v-click class="transition-all duration-500">

## 2. Generator

Generate Model, Factory, Controller, Request, and Routes from reading a database
table.

```bash
# Example for a 'posts' table
php artisan inertia-builder:generate posts
```

Then recompile the frontend:

```bash
npm run dev
```
</div>

---
layout: 'intro'
---

# Thank You!

Q&A

jardik.oryza@gmail.com
