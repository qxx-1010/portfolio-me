# Empty state guidelines

The EmptyState component is a generic component that gives feedback to an end-user in case there is no data available. Here is the guidance on writing your empty states.

## Content guidelines

- An empty state title should be short, concise, and tell the user about the issue or current situation in one sentence.
- Don't use punctuation in empty state titles.
- Provide details when the user needs more context to solve the empty state. Explain the solution with straightforward language.
- Keep the details to one or two sentences.
- Avoid repeating the title in the details.
- For the action button, make the button label match the action the user will take. Keep the button label to one or two words. [Buttons guidelines](/design/components/buttons/Button).
- If a footer is necessary, provide the user with helpful, relevant links such as documentation or support articles. [Links guidelines](/design/components/typography/Link).
- Don't apologize in an empty state.
- If there's an illustration in the empty state, add an `arial-label` for accessibility.

## Use cases

When designing your empty states, consider the following use cases. The `EmptyState` component includes a dedicated illustration for each use case.

### Something missing

#### Scenarios
- The user hasn't configured or enabled a setting or feature, and the data can't be displayed.

#### Recommended content structure
- **Title**: What's missing or what's not configured?
- **Details**: How can the missing item be fixed? If there's no solution, provide the user with a return path.
- **Actions**: Based on context.
- **Footer**: Relevant links such as documentation or support articles, if applicable.

#### Example
![empty-state-missing-configuration-light-6064fcefd5fe14e417fdc31e6dbefdf2](https://github.com/user-attachments/assets/f35fa83c-27da-4928-8e84-be6632b0519b)


### No result

#### Scenarios
- No matching results for the keywords/filters/parameters used.
- No results available (identifiable or unknown reason).
- No matching results because of missing permissions.
- The page doesn't exist or isn't available (404).

#### Recommended content structure
- **Title**: What result or data can't the system find?
- **Details**: How to fix the state? Guide the user in adjusting filters, keywords, timeframe, etc.
- **Actions**: Based on context.
- **Footer**: Relevant links such as documentation or support articles, if applicable.

#### Example
![empty-state-search-conditions-light-5d4e7cb24c1169dc771eda131f959045](https://github.com/user-attachments/assets/dbc94a06-6863-4d62-8694-2317bc66de97)


### Something is wrong

#### Scenarios
- The system can’t load the data due to an error (identifiable or unknown).
- The user performed an action that triggered an error.
- The page doesn't exist or isn't available (404).

#### Recommended content structure
- **Title**: What's the issue?
- **Details**: Describe the cause of the issue or the error code and possible solutions. If no solution is available, provide the user with a return path.
- **Actions**: Based on context, including “Refresh,” “Try again,” or “Go back,” etc.
- **Footer**: Relevant links such as documentation or support articles, if applicable.

#### Example
![empty-state-system-error-light-4f0c2d33bef300745985373d5a1ff510](https://github.com/user-attachments/assets/992d6957-1d04-48bf-b516-b2faa9cacacf)


### Create new

#### Scenarios
- The user visits the page for the first time, and no items/data have yet been created.
- The user needs to select the existing item or add, upload, or create an item/data.

#### Recommended content structure
- **Title**: What's the current state? What hasn't been created?
- **Details**: Describe what needs to be created and guidance or requirements for the creation.
- **Actions**: Based on context, including “Create,” “Get started,” or “Upload,” etc.
- **Footer**: Relevant links such as documentation or support articles, if applicable.

#### Example
![empty-state-first-time-use-light-7dd43b3483544f7b4a56b05f4d9cbdf5](https://github.com/user-attachments/assets/260467ab-a681-4c4d-add8-88582a09cba9)


### No permission

#### Scenarios
- The user has limited or no permissions to create/view/edit data.

#### Recommended content structure
- **Title**: What permission is missing?
- **Details**: Provide a possible solution to get the permission. If no solution is available, provide the user with a return path.
- **Actions**: Based on context, including “Contact admin” or “Go back.”
- **Footer**: Relevant links such as documentation or support articles, if applicable.

#### Example
![empty-state-limited-permission-light-dbe23e71709e66a3ef4c0a704476d439](https://github.com/user-attachments/assets/7068ef26-c3e6-44a2-a850-99411c1196c6)

