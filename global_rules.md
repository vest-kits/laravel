You are an expert in PHP, Laravel, React, Inertia, Blade, Pest, and Tailwind.
Always use Laravel version specified in composer.json to make sure to use the latest features.

1. Coding Standards

- Utilize the latest PHP v8.4 features.
- Adhere to coding standards defined in `pint.json`.
- Enforce strict type safety, including `array` shapes using PHPStan.

2. Project Structure & Architecture

- Remove the existing `.gitkeep` file when creating a new file.
- Follow the existing project structure; do not create additional folders.
- Do not use the `DB::` facade directly—always use `Model::query()`.
- Do not add, update, or delete dependencies without prior approval.

2.1 Directory Conventions

`app/Http/Controllers` - Controllers
- Do not use abstract `Controller.php` or any base controller.

`app/Http/Requests` - Form Requests
- Always use FormRequest for validation.
- Use `Create`, `Update`, and `Delete` verbs in naming.

`app/Actions` - Business Logic
- Follow the Actions pattern.
- Use `Create`, `Update`, and `Delete` verbs in naming.
- Example Implementation:
    ```php
    public function store(CreateTodoRequest $request, CreateTodoAction $action)
    {
        /** @var User $user */
        $user = $request->user();

        $action->handle($user, $request->validated());
        
        // ...
    }
    ```

`app/Models` - Eloquent Models
- Do not use `fillable` in models.
- Unguarded models are preferred. 
- Example Implementation in `AppServiceProvider`:
    ```php
    public function boot(): void
    {
        Model::unguard();
        Model::preventLazyLoading(!app()->environment('production'));
    }
    ```

3. Testing

- All tests must be written using PEST PHP.
- Run `composer lint` after creating or modifying a file.
- Run `composer test` before finalizing any changes to ensure tests pass.
- Always confirm with approval before removing a test.
- Ensure all new code is covered by tests.
- When creating models, always generate a `{Model}Factory`.

3.1 Test Directory Structure

- Commands: tests/Feature/Console
- Controllers: tests/Feature/Http
- Actions: tests/Unit/Actions
- Models: tests/Unit/Models
- Jobs: tests/Unit/Jobs

4. Styling & UI

- Tailwind CSS must be used for styling.
- Maintain a minimal UI design.

5. Task Completion Requirements

- Recompile assets after making frontend-related changes.
- Ensure compliance with all above guidelines before marking a task as complete.
