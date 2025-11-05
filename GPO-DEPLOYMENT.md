# Enterprise Deployment via Active Directory GPO

This guide covers deploying custom mouse cursors across domain-joined computers using Active Directory Group Policy Objects.

## Prerequisites

- Active Directory Domain Services
- Group Policy Management Console (GPMC)
- Domain Administrator privileges
- Cursor files stored in SYSVOL or accessible location

## Step-by-Step Deployment

### 1. Prepare Cursor Files

1. **Copy** cursor files to: `\\domain.com\SYSVOL\domain.com\Policies\{GPO-GUID}\Machine\cursors\`
2. **Alternative**: Store in any location accessible during GPO processing

### 2. Create Group Policy Object

1. **Open** Group Policy Management Console
2. **Right-click** target OU → `Create a GPO in this domain, and Link it here`
3. **Name** the GPO: `Custom Mouse Cursors`
4. **Right-click** the new GPO → `Edit`

### 3. Deploy Cursor Files

Navigate to: `Computer Configuration` → `Preferences` → `Windows Settings` → `Files`

**Create file items for each cursor by right-clicking in the empty white space and click New > File:**

#### File 1: Normal Select Cursor

- **Action**: Create
- **Source file(s)**: `\\path where you copied the cursors\Normal Select.cur`
- **Destination file**: `C:\Windows\Cursors\Archaeological\Normal Select.cur`

#### File 2: Help Select Cursor

- **Action**: Create
- **Source file(s)**: `\\path where you copied the cursors\Help Select.cur`
- **Destination file**: `C:\Windows\Cursors\Archaeological\Help Select.cur`

#### File 3: Working in Background Cursor

- **Action**: Create
- **Source file(s)**: `\\path where you copied the cursors\Working in Background.ani`
- **Destination file**: `C:\Windows\Cursors\Archaeological\Working in Background.ani`

#### File 4: Busy Cursor

- **Action**: Create
- **Source file(s)**: `\\path where you copied the cursors\Busy.ani`
- **Destination file**: `C:\Windows\Cursors\Archaeological\Busy.ani`

#### File 5: Text Select Cursor

- **Action**: Create
- **Source file(s)**: `\\path where you copied the cursors\Text Select.cur`
- **Destination file**: `C:\Windows\Cursors\Archaeological\Text Select.cur`

#### File 6: Handwriting Cursor

- **Action**: Create
- **Source file(s)**: `\\path where you copied the cursors\Handwriting.cur`
- **Destination file**: `C:\Windows\Cursors\Archaeological\Handwriting.cur`

#### File 7: Link Select Cursor

- **Action**: Create
- **Source file(s)**: `\\path where you copied the cursors\Link Select.cur`
- **Destination file**: `C:\Windows\Cursors\Archaeological\Link Select.cur`

### 4. Configure Registry Settings

Navigate to: `Computer Configuration` → `Preferences` → `Windows Settings` → `Registry`

**Create these registry items:**

#### Normal Select Cursor

- **Action**: Update
- **Hive**: HKEY_CURRENT_USER
- **Key Path**: `Control Panel\Cursors`
- **Value Name**: `Arrow`
- **Value Type**: REG_SZ
- **Value Data**: `C:\Windows\Cursors\Archaeological\Normal Select.cur`

#### Help Select Cursor

- **Action**: Update
- **Hive**: HKEY_CURRENT_USER
- **Key Path**: `Control Panel\Cursors`
- **Value Name**: `Help`
- **Value Type**: REG_SZ
- **Value Data**: `C:\Windows\Cursors\Archaeological\Help Select.cur`

#### Working in Background Cursor

- **Action**: Update
- **Hive**: HKEY_CURRENT_USER
- **Key Path**: `Control Panel\Cursors`
- **Value Name**: `AppStarting`
- **Value Type**: REG_SZ
- **Value Data**: `C:\Windows\Cursors\Archaeological\Working in Background.ani`

#### Busy Cursor

- **Action**: Update
- **Hive**: HKEY_CURRENT_USER
- **Key Path**: `Control Panel\Cursors`
- **Value Name**: `Wait`
- **Value Type**: REG_SZ
- **Value Data**: `C:\Windows\Cursors\Archaeological\Busy.ani`

#### Text Select Cursor

- **Action**: Update
- **Hive**: HKEY_CURRENT_USER
- **Key Path**: `Control Panel\Cursors`
- **Value Name**: `IBeam`
- **Value Type**: REG_SZ
- **Value Data**: `C:\Windows\Cursors\Archaeological\Text Select.cur`

#### Handwriting Cursor

- **Action**: Update
- **Hive**: HKEY_CURRENT_USER
- **Key Path**: `Control Panel\Cursors`
- **Value Name**: `Crosshair`
- **Value Type**: REG_SZ
- **Value Data**: `C:\Windows\Cursors\Archaeological\Handwriting.cur`

#### Link Select Cursor

- **Action**: Update
- **Hive**: HKEY_CURRENT_USER
- **Key Path**: `Control Panel\Cursors`
- **Value Name**: `Hand`
- **Value Type**: REG_SZ
- **Value Data**: `C:\Windows\Cursors\Archaeological\Link Select.cur`

### 5. Force Policy Update

**On client machines:**

```cmd
gpupdate /force
```

**Or wait for automatic refresh** (90-120 minutes)

## Security Benefits

- **No network shares required** - Files deployed directly via GPO
- **No file permissions to manage** - Uses SYSVOL security model
- **Centralized management** - All configuration in single GPO
- **Atomic deployment** - Files and registry settings applied together

## Verification

### Check Policy Application

```cmd
gpresult /r
rsop.msc
```

### Verify Registry Changes

```cmd
reg query "HKCU\Control Panel\Cursors"
```
