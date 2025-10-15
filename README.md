# supabase_expo_tryout
Testing the first connection between supabase and expo project

## Step-by-step

1. Create [Expo project](https://expo.dev/)
2. In the development computer run the following commands in the following order\
`npm install -g expo-cli`\
`expo init <app-name>`
This last command will show two (2) options, for this project the chosen option was
`Blank (typescript)`
3. Installing app dependencies
```
npm install @supabase/supabase-js
npx expo install @react-native-async-storage/async-storage
npm install react-native-url-polyfill
```

# Connecting Supabase to Expo snack

## Create a supabase.js file for credential
```
import { createClient } from '@supabase/supabase-js';

// Replace with your own Supabase project details
const SUPABASE_URL = 'https://adbyufdohfqmjceaiwvt.supabase.co';
const SUPABASE_ANON_KEY = 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6ImFkYnl1ZmRvaGZxbWpjZWFpd3Z0Iiwicm9sZSI6ImFub24iLCJpYXQiOjE3NjAyODUyMTgsImV4cCI6MjA3NTg2MTIxOH0.h3QxTgMBEpixT5Ch00RKGhoFwYE10N1Y9u_5P9a4iw4';

export const supabase = createClient(SUPABASE_URL, SUPABASE_ANON_KEY);
```
## Inside app.js

```
import { supabase } from './supabase'; // make sure path is correct
const { data, error } = await supabase.from('base data').select('*');
```

Until here, the data will **NOT** be retrived, because of limitations from supabase part

## Enabling Data reading from supabase
- log into the database and table >> RSS policy
- Create New Policy with the following commands
Public Name: Public connection
Table: <table name>
Policy Behaviour: Permissive
Policy Command: Select
Target Roles: Defaults to all
Using: True


