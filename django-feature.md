# /django-feature — Scaffold a complete Django feature

Plan and implement a full Django feature end-to-end following the project's conventions.

## Arguments

$ARGUMENTS — Description of the feature to build (e.g., "add a wishlist app where users can save items they want")

## Steps

### 1. Plan
- Read existing apps to understand the project's patterns and conventions.
- Identify which app this belongs to (existing or new).
- List the models, fields, and relationships needed.
- List the views (CRUD pattern: list, detail, create, edit, delete).
- Identify template files needed.
- Present the plan to the user for approval before writing code.

### 2. Model
- Define models with appropriate fields and relationships.
- Include `created_at = DateTimeField(auto_now_add=True)` for timestamps.
- Include a ForeignKey to User for attribution (e.g., `created_by`).
- Add sensible `Meta.ordering`.
- Register in admin.

### 3. Form
- Create ModelForm(s) excluding auto-set fields (`created_by`, `created_at`, etc.).

### 4. Views
- Use `@login_required` on all views.
- Use `get_object_or_404()` for lookups.
- Set `created_by = request.user` on creation.
- Redirect after successful POST.

### 5. URLs
- Use `app_name` for namespacing.
- Follow existing naming convention (e.g., `<model>_list`, `<model>_create`, `<model>_detail`).

### 6. Templates
- Extend the base template.
- Match the existing UI framework and layout patterns.
- Include CSRF tokens in all forms.
- Add confirmation step for delete actions.

### 7. Wiring
- Add app to `INSTALLED_APPS` if new app.
- Add URL include if new app.
- Add navigation link if user-facing.

### 8. Migration
- Run `makemigrations` then `migrate`.

### 9. Tests
- Write tests covering: list view returns 200, create via POST works, object is persisted, delete works.
- Use existing test fixtures and patterns from the project.

### 10. Quality
- Format, lint, and run the full test suite.

## Rules
- Always present the plan before writing code.
- Follow existing patterns — read similar features first.
- Don't over-engineer; keep it consistent with the rest of the codebase.
