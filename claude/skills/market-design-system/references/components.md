# Market Components Reference

## Component Architecture

Market uses Web Components (Custom Elements) with the `market-` prefix. Components are:
- Framework-agnostic (work with React, Vue, Angular, vanilla JS)
- Self-contained with Shadow DOM encapsulation
- Theme-aware via CSS custom properties

## Storybook Navigation

**Base URL**: `https://market-storybook.s3.amazonaws.com/2.10.0/index.html`

**URL Pattern**: `?path=/docs/components-market-{component}--{story}`

Example: `?path=/docs/components-market-accordion-item--basic-example`

---

## Component Categories

### Buttons & Actions

#### `<market-button>`
Primary interactive element for actions.

```html
<!-- Primary (default) -->
<market-button>Submit</market-button>

<!-- Secondary -->
<market-button variant="secondary">Cancel</market-button>

<!-- Destructive -->
<market-button variant="destructive">Delete</market-button>

<!-- Loading state -->
<market-button loading>Saving...</market-button>

<!-- Disabled -->
<market-button disabled>Unavailable</market-button>

<!-- With icon -->
<market-button>
  <market-icon slot="icon" name="plus"></market-icon>
  Add Item
</market-button>
```

**Props**:
- `variant`: "primary" | "secondary" | "destructive"
- `size`: "small" | "medium" | "large"
- `loading`: boolean
- `disabled`: boolean

---

### Form Inputs

#### `<market-input-text>`
Text input field with label and validation.

```html
<!-- Basic -->
<market-input-text label="Full Name"></market-input-text>

<!-- With placeholder -->
<market-input-text 
  label="Email" 
  placeholder="you@example.com"
  type="email">
</market-input-text>

<!-- Required with error -->
<market-input-text 
  label="Username"
  required
  error="Username is required">
</market-input-text>

<!-- With helper text -->
<market-input-text 
  label="Password"
  type="password"
  helper="Must be at least 8 characters">
</market-input-text>

<!-- Disabled -->
<market-input-text 
  label="Account ID"
  value="ACC-12345"
  disabled>
</market-input-text>
```

**Props**:
- `label`: string (required)
- `type`: "text" | "email" | "password" | "tel" | "url" | "number"
- `placeholder`: string
- `value`: string
- `required`: boolean
- `disabled`: boolean
- `error`: string (validation message)
- `helper`: string (help text)

#### `<market-select>`
Dropdown selection.

```html
<market-select label="Country">
  <market-option value="us">United States</market-option>
  <market-option value="ca">Canada</market-option>
  <market-option value="mx">Mexico</market-option>
</market-select>
```

#### `<market-checkbox>`
```html
<market-checkbox>Accept terms and conditions</market-checkbox>
<market-checkbox checked>Remember me</market-checkbox>
<market-checkbox indeterminate>Select all</market-checkbox>
```

#### `<market-radio>` / `<market-radio-group>`
```html
<market-radio-group label="Payment Method">
  <market-radio value="card">Credit Card</market-radio>
  <market-radio value="bank">Bank Account</market-radio>
  <market-radio value="cash">Cash</market-radio>
</market-radio-group>
```

#### `<market-toggle>`
```html
<market-toggle>Enable notifications</market-toggle>
<market-toggle checked>Dark mode</market-toggle>
```

#### `<market-textarea>`
```html
<market-textarea 
  label="Description"
  placeholder="Enter a description..."
  rows="4">
</market-textarea>
```

---

### Layout Components

#### `<market-accordion>` / `<market-accordion-item>`
Collapsible content sections.

```html
<market-accordion>
  <market-accordion-item>
    <span slot="label">Section 1</span>
    <p>Content for section 1...</p>
  </market-accordion-item>
  <market-accordion-item>
    <span slot="label">Section 2</span>
    <p>Content for section 2...</p>
  </market-accordion-item>
</market-accordion>
```

#### `<market-card>`
Content container with optional header/footer.

```html
<market-card>
  <h3 slot="header">Card Title</h3>
  <p>Card content goes here...</p>
  <div slot="footer">
    <market-button variant="secondary">Cancel</market-button>
    <market-button>Save</market-button>
  </div>
</market-card>
```

#### `<market-modal>`
Dialog overlay.

```html
<market-modal open>
  <h2 slot="header">Confirm Action</h2>
  <p>Are you sure you want to proceed?</p>
  <div slot="footer">
    <market-button variant="secondary" data-dismiss>Cancel</market-button>
    <market-button variant="destructive">Delete</market-button>
  </div>
</market-modal>
```

**Props**:
- `open`: boolean
- `dismissable`: boolean (show close button)
- `size`: "small" | "medium" | "large" | "fullscreen"

#### `<market-drawer>`
Side panel overlay.

```html
<market-drawer open position="right">
  <h2 slot="header">Settings</h2>
  <!-- drawer content -->
</market-drawer>
```

**Props**:
- `open`: boolean
- `position`: "left" | "right"

#### `<market-tabs>` / `<market-tab>` / `<market-tab-panel>`
Tabbed interface.

```html
<market-tabs>
  <market-tab slot="tab" panel="overview">Overview</market-tab>
  <market-tab slot="tab" panel="details">Details</market-tab>
  <market-tab slot="tab" panel="history">History</market-tab>
  
  <market-tab-panel name="overview">
    Overview content...
  </market-tab-panel>
  <market-tab-panel name="details">
    Details content...
  </market-tab-panel>
  <market-tab-panel name="history">
    History content...
  </market-tab-panel>
</market-tabs>
```

---

### Feedback Components

#### `<market-toast>`
Temporary notification.

```html
<market-toast variant="success" duration="5000">
  Changes saved successfully!
</market-toast>

<market-toast variant="error">
  Failed to save changes.
</market-toast>
```

**Props**:
- `variant`: "info" | "success" | "warning" | "error"
- `duration`: number (ms, 0 for persistent)
- `dismissable`: boolean

#### `<market-banner>`
Persistent alert/notification.

```html
<market-banner variant="warning">
  Your subscription expires in 3 days.
  <market-button slot="action" variant="secondary">Renew</market-button>
</market-banner>
```

**Props**:
- `variant`: "info" | "success" | "warning" | "error"
- `dismissable`: boolean

#### `<market-tooltip>`
Contextual help on hover/focus.

```html
<market-tooltip content="Click to save your changes">
  <market-button>Save</market-button>
</market-tooltip>
```

#### `<market-loading>` / `<market-spinner>`
Loading indicators.

```html
<!-- Spinner -->
<market-spinner size="medium"></market-spinner>

<!-- Full loading state -->
<market-loading>Loading data...</market-loading>
```

---

### Navigation Components

#### `<market-header>`
Page/section header.

```html
<market-header>
  <h1 slot="title">Dashboard</h1>
  <market-button slot="actions">New Item</market-button>
</market-header>
```

#### `<market-breadcrumb>` / `<market-breadcrumb-item>`
```html
<market-breadcrumb>
  <market-breadcrumb-item href="/">Home</market-breadcrumb-item>
  <market-breadcrumb-item href="/products">Products</market-breadcrumb-item>
  <market-breadcrumb-item>Current Page</market-breadcrumb-item>
</market-breadcrumb>
```

#### `<market-pagination>`
```html
<market-pagination 
  total="100" 
  page-size="10" 
  current-page="1">
</market-pagination>
```

---

### Data Display

#### `<market-table>`
Data table with sorting/selection.

```html
<market-table>
  <market-table-header>
    <market-table-row>
      <market-table-cell header sortable>Name</market-table-cell>
      <market-table-cell header sortable>Date</market-table-cell>
      <market-table-cell header>Status</market-table-cell>
    </market-table-row>
  </market-table-header>
  <market-table-body>
    <market-table-row>
      <market-table-cell>John Doe</market-table-cell>
      <market-table-cell>2024-01-15</market-table-cell>
      <market-table-cell>Active</market-table-cell>
    </market-table-row>
  </market-table-body>
</market-table>
```

#### `<market-badge>`
Status indicator.

```html
<market-badge variant="success">Active</market-badge>
<market-badge variant="warning">Pending</market-badge>
<market-badge variant="error">Failed</market-badge>
```

#### `<market-avatar>`
User/entity representation.

```html
<market-avatar src="/user.jpg" alt="John Doe"></market-avatar>
<market-avatar initials="JD"></market-avatar>
```

---

## Common Patterns

### Form with Validation
```html
<form>
  <market-input-text 
    label="Email" 
    type="email" 
    required
    id="email">
  </market-input-text>
  
  <market-input-text 
    label="Password" 
    type="password" 
    required
    helper="Minimum 8 characters"
    id="password">
  </market-input-text>
  
  <market-checkbox required>
    I agree to the Terms of Service
  </market-checkbox>
  
  <market-button type="submit">Sign Up</market-button>
</form>
```

### Confirmation Modal
```html
<market-modal id="confirm-delete">
  <h2 slot="header">Delete Item?</h2>
  <p>This action cannot be undone. Are you sure you want to delete this item?</p>
  <div slot="footer">
    <market-button variant="secondary" data-dismiss>Cancel</market-button>
    <market-button variant="destructive" id="confirm-btn">Delete</market-button>
  </div>
</market-modal>
```

### Empty State
```html
<market-card>
  <div class="empty-state">
    <market-icon name="inbox" size="large"></market-icon>
    <h3>No items yet</h3>
    <p>Get started by creating your first item.</p>
    <market-button>Create Item</market-button>
  </div>
</market-card>
```

### Loading State
```html
<market-card>
  <market-loading>
    <p>Loading your data...</p>
  </market-loading>
</market-card>
```

---

## Event Handling

Market components emit custom events:

```javascript
// Button click
document.querySelector('market-button').addEventListener('click', (e) => {
  console.log('Button clicked');
});

// Input change
document.querySelector('market-input-text').addEventListener('market-input-change', (e) => {
  console.log('New value:', e.detail.value);
});

// Modal close
document.querySelector('market-modal').addEventListener('market-modal-close', (e) => {
  console.log('Modal closed');
});

// Tab change
document.querySelector('market-tabs').addEventListener('market-tab-change', (e) => {
  console.log('Active tab:', e.detail.panel);
});
```

## React Integration

```jsx
import { MarketButton, MarketInputText } from '@aspect/market-react';

function MyForm() {
  const [email, setEmail] = useState('');
  
  return (
    <form>
      <MarketInputText
        label="Email"
        type="email"
        value={email}
        onMarketInputChange={(e) => setEmail(e.detail.value)}
      />
      <MarketButton onClick={handleSubmit}>
        Submit
      </MarketButton>
    </form>
  );
}
```
