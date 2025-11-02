# Figma to Code - Example Workflows

This file contains practical examples of the Figma to Code skill in action.

## Example 1: Button Reuse

**User**: "Create this button: node-id=123:456"

**Process:**
1. `get_metadata(123:456)` → "Button/Primary/Large"
2. `get_design_context(123:456)` → colors/iris/950, padding 16px 24px
3. Search: `Glob("components/ui/button.tsx")` → Found
4. Read: Has variant="primary" and size="lg"

**Output:**
```tsx
import { Button } from "[COMPONENTS_DIR]/ui/button"

<Button variant="primary" size="lg">Button Text</Button>
// No new component needed
```

---

## Example 2: Card Composition

**User**: "Implement this product card from node 789:012"

**Process:**
1. `get_metadata(789:012)` → "ProductCard" with Image, Title, Description, Price, Button
2. `get_design_context(789:012)` → Card styling, color tokens
3. Check: `components/ui/card.tsx` exists → Use composition

**Output:**
```tsx
import { Card, CardContent, CardFooter, CardHeader, CardTitle } from "[COMPONENTS_DIR]/ui/card"
import { Button } from "[COMPONENTS_DIR]/ui/button"
import Image from "next/image"

interface ProductCardProps {
  title: string
  description: string
  price: number
  imageUrl: string
}

export function ProductCard({ title, description, price, imageUrl }: ProductCardProps) {
  return (
    <Card className={[CARD_STYLES]}>
      <div className={[IMAGE_CONTAINER_STYLES]}>
        <Image src={imageUrl} alt={title} fill className={[IMAGE_STYLES]} />
      </div>
      <CardHeader><CardTitle>{title}</CardTitle></CardHeader>
      <CardContent>
        <p className={[DESCRIPTION_STYLES]}>{description}</p>
        <p className={[PRICE_STYLES]}>${price}</p>
      </CardContent>
      <CardFooter>
        <Button variant="primary" className={[BUTTON_STYLES]}>Add to Cart</Button>
      </CardFooter>
    </Card>
  )
}
```

---

## Example 3: Page with Backend Requirements

**User**: "Create dashboard page from node 100:200"

**Process:**
1. `get_metadata(100:200)` → Page with Stats Grid showing revenue, users
2. Recognize: Needs backend API for dynamic data
3. Ask user about backend implementation approach

**Ask user:**
```
⚠️ Backend Change Required

Dashboard needs API for stats (revenue, users, conversion).

Would you like:
1. Frontend with mocked data (recommended)
2. Both frontend and backend
3. Frontend only with API documentation
```

**If user chooses option 1 (mock data):**

```tsx
// [PAGES_DIR]/dashboard/page.tsx
import { Card, CardContent, CardHeader, CardTitle } from "[COMPONENTS_DIR]/ui/card"

// TODO: Replace with [BACKEND_DIR]/[API_MODULE] API
const mockStats = { revenue: 45231.89, users: 2350 }

/**
 * Backend API Required:
 * GET /api/dashboard/stats
 * Response: { revenue: number, users: number }
 */
export default function DashboardPage() {
  const stats = mockStats
  return (
    <div className={[CONTAINER_STYLES]}>
      <div className={[GRID_STYLES]}>
        <Card>
          <CardHeader><CardTitle className={[LABEL_STYLES]}>Revenue</CardTitle></CardHeader>
          <CardContent>
            <div className={[VALUE_STYLES]}>${stats.revenue.toLocaleString()}</div>
          </CardContent>
        </Card>
        <Card>
          <CardHeader><CardTitle className={[LABEL_STYLES]}>Users</CardTitle></CardHeader>
          <CardContent>
            <div className={[VALUE_STYLES]}>{stats.users.toLocaleString()}</div>
          </CardContent>
        </Card>
      </div>
    </div>
  )
}
```

---

## Example 4: Creating New Component with Variants

**User**: "Create this status badge from Figma node 456:789"

**Process:**
1. `get_metadata(456:789)` → "StatusBadge" with variants: success, warning, error
2. `get_design_context(456:789)` → Different colors per variant
3. Check: No exact match in `components/ui/badge.tsx`
4. Ask user if should extend Badge or create new component
5. User approves creating new component

**Output:**
```tsx
import * as React from "react"
import { [STYLING_UTILITY] } from "[UTILITY_PATH]"

const statusBadgeVariants = [VARIANT_SYSTEM_IMPLEMENTATION]
// Example variants:
// - success: Use your project's success color tokens
// - warning: Use your project's warning color tokens
// - error: Use your project's error color tokens

interface StatusBadgeProps extends React.HTMLAttributes<HTMLSpanElement> {
  status?: "success" | "warning" | "error"
}

export const StatusBadge = React.forwardRef<HTMLSpanElement, StatusBadgeProps>(
  ({ className, status = "success", ...props }, ref) => {
    return (
      <span
        ref={ref}
        className={[APPLY_VARIANT_STYLES]}
        {...props}
      />
    )
  }
)

StatusBadge.displayName = "StatusBadge"
```

**Usage:**
```tsx
<StatusBadge status="success">Active</StatusBadge>
<StatusBadge status="warning">Pending</StatusBadge>
<StatusBadge status="error">Failed</StatusBadge>
```

---

## Example 5: Full Page Layout

**User**: "Implement this settings page from Figma node 999:111"

**Process:**
1. `get_metadata(999:111)` → Settings page with tabs: Profile, Notifications, Security
2. `get_design_context` for each section
3. Check existing: PageLayout, Tabs, Form components available
4. Generate using composition

**Output:**
```tsx
// [PAGES_DIR]/settings/page.tsx
import { Tabs, TabsContent, TabsList, TabsTrigger } from "[COMPONENTS_DIR]/ui/tabs"
import { PageHeader, PageTitle, PageDescription } from "[COMPONENTS_DIR]/ui/page-layout"
import { Card, CardContent, CardDescription, CardHeader, CardTitle } from "[COMPONENTS_DIR]/ui/card"
import { Label } from "[COMPONENTS_DIR]/ui/label"
import { Input } from "[COMPONENTS_DIR]/ui/input"
import { Button } from "[COMPONENTS_DIR]/ui/button"
import { Switch } from "[COMPONENTS_DIR]/ui/switch"

export default function SettingsPage() {
  return (
    <div className={[CONTAINER_STYLES]}>
      <PageHeader>
        <PageTitle>Settings</PageTitle>
        <PageDescription>Manage your account settings and preferences</PageDescription>
      </PageHeader>

      <Tabs defaultValue="profile" className={[TABS_CONTAINER_STYLES]}>
        <TabsList>
          <TabsTrigger value="profile">Profile</TabsTrigger>
          <TabsTrigger value="notifications">Notifications</TabsTrigger>
          <TabsTrigger value="security">Security</TabsTrigger>
        </TabsList>

        <TabsContent value="profile" className={[TAB_CONTENT_STYLES]}>
          <Card>
            <CardHeader>
              <CardTitle>Profile Information</CardTitle>
              <CardDescription>Update your personal details</CardDescription>
            </CardHeader>
            <CardContent className={[FORM_CONTAINER_STYLES]}>
              <div className={[FORM_FIELD_STYLES]}>
                <Label htmlFor="name">Name</Label>
                <Input id="name" placeholder="Enter your name" />
              </div>
              <div className={[FORM_FIELD_STYLES]}>
                <Label htmlFor="email">Email</Label>
                <Input id="email" type="email" placeholder="Enter your email" />
              </div>
              <Button>Save Changes</Button>
            </CardContent>
          </Card>
        </TabsContent>

        <TabsContent value="notifications" className={[TAB_CONTENT_STYLES]}>
          <Card>
            <CardHeader>
              <CardTitle>Notification Preferences</CardTitle>
              <CardDescription>Manage how you receive notifications</CardDescription>
            </CardHeader>
            <CardContent className={[FORM_CONTAINER_STYLES]}>
              <div className={[SETTING_ROW_STYLES]}>
                <div className={[SETTING_INFO_STYLES]}>
                  <Label>Email Notifications</Label>
                  <p className={[DESCRIPTION_STYLES]}>
                    Receive notifications via email
                  </p>
                </div>
                <Switch />
              </div>
              <div className={[SETTING_ROW_STYLES]}>
                <div className={[SETTING_INFO_STYLES]}>
                  <Label>Push Notifications</Label>
                  <p className={[DESCRIPTION_STYLES]}>
                    Receive push notifications
                  </p>
                </div>
                <Switch />
              </div>
            </CardContent>
          </Card>
        </TabsContent>

        <TabsContent value="security" className={[TAB_CONTENT_STYLES]}>
          <Card>
            <CardHeader>
              <CardTitle>Security Settings</CardTitle>
              <CardDescription>Manage your account security</CardDescription>
            </CardHeader>
            <CardContent className={[FORM_CONTAINER_STYLES]}>
              <div className={[FORM_FIELD_STYLES]}>
                <Label htmlFor="current-password">Current Password</Label>
                <Input id="current-password" type="password" />
              </div>
              <div className={[FORM_FIELD_STYLES]}>
                <Label htmlFor="new-password">New Password</Label>
                <Input id="new-password" type="password" />
              </div>
              <Button>Update Password</Button>
            </CardContent>
          </Card>
        </TabsContent>
      </Tabs>
    </div>
  )
}
```

---

## Common Patterns

### Pattern: Extending Existing Component

When existing component is close but needs small tweaks:

```tsx
// Use className prop for minor customizations
<Button variant="primary" className={[ADDITIONAL_STYLES]}>
  Custom Styled Button
</Button>

// Or create wrapper component
export function RoundedButton(props: ButtonProps) {
  return <Button {...props} className={[MERGE_STYLES]} />
}
```

### Pattern: Composition over Creation

Always check if multiple existing components can achieve the design:

```tsx
// Instead of creating "AlertCard" component
// Compose Alert + Card
<Card>
  <CardContent className="pt-6">
    <Alert>
      <AlertCircle className="h-4 w-4" />
      <AlertTitle>Heads up!</AlertTitle>
      <AlertDescription>Important message here</AlertDescription>
    </Alert>
  </CardContent>
</Card>
```

### Pattern: Mock Data Documentation

Always document backend requirements clearly:

```tsx
// TODO: Replace with backend API
const mockData = [ /* ... */ ]

/**
 * Backend API Required:
 * GET /api/endpoint
 * Response: { field: type }
 * Backend file: [BACKEND_DIR]/[API_MODULE]/routes.ts
 */
```
