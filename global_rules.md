You are an expert in PHP, Laravel, React, Inertia, Pest, and Tailwind.

# Coding Standards:
- Use the latest PHP 8.4 features.
- Use `pint.json` for coding standards.
- Be strict with types, including array shapes using PHPStan.

# Project Structure & Architecture

- When creating a new file, remove the existing `.gitkeep` file.
- Stick the existing project structure, never create additional folders.
- Don't use the `DB::` facade directly, use `Model::query()` instead.
- Never add / update / delete a dependency without asking me first.

- `app/Http/Controllers` - Controllers.
    - Don't use the abstract `Controller.php`, or any other base controller.

- `app/Http/Requests` - Form requests.
    - Always use FormRequest for validation, and use `Create`, `Update` and `Delete` verbs.

- `app/Actions` - Business logic.
    - Always use the actions pattern, and use `Create`, `Update` and `Delete` verbs.

- `app/Models` - Eloquent models.
    - Don't use `fillable` in models.

E.g:
```
public function store(CreateTodoRequest $request, CreateTodoAction $action)
{
    /** @var User $user */
    $user = $request->user();

    $action->handle($user, $request->validated());
    
    // ...
}
```

# Testing
- Always write tests using PEST PHP.
- Run `composer lint` after creating or modifying a file.
- Run `composer test` at the very end to ensure all tests pass.
- Always ask me for clarification if you think you should remove a test.
- Always make sure the new code is covered by tests.
- When creating models, always create a factory.
- Put models testing in the `tests/Unit/Models` directory.
- Put actions testing in the `tests/Unit/Actions` directory.
- Put controllers testing in the `tests/Feature` directory.

# Styling & UI
- Use Tailwind CSS for styling.
- Use a very minimal UI design.

# Ending tasks
- But sure to re-compile assets after finishing a task that involves frontend changes.
