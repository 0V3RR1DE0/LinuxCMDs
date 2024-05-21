# LinuxCMDs
```
curl -o asenna_taustaohjelma.sh https://gist.githubusercontent.com/0V3RR1DE0/a87e12093043d04d68652707b87cc66b/raw/asenna_taustaohjelma.sh && chmod +x asenna_taustaohjelma.sh && sudo ./asenna_taustaohjelma.sh
```


---

```
#!/bin/bash

# Group name
GROUP_NAME="Ohjelmointi"

# Node name
NODE_NAME="kelab08"

# Role name
ROLE_NAME="Ohjelmointi"

# Function to add permissions for VMs
add_vm_permissions() {
    local vm_id=$1
    
    # Create ACL for VM
    pvesh set /access/acl -path "/vms/${vm_id}" -roles "${ROLE_NAME}" -groups "${GROUP_NAME}"
    
    # Check if ACL addition was successful
    if [ $? -eq 0 ]; then
        echo "Permissions added for VM: ${vm_id}"
    else
        echo "Failed to add permissions for VM: ${vm_id}"
    fi
}

# VM list
VM_LIST=(
    "120"
    "200"
    "121"
    # Add more VM IDs here
)

# Loop through VMs and add permissions
for vm_id in "${VM_LIST[@]}"; do
    add_vm_permissions "${vm_id}"
done

echo "All permissions added successfully."
```

---

```
import React, { useState, useEffect } from 'react';

const MaliciousComponent = () => {
  const [hidden, setHidden] = useState(true);

  useEffect(() => {
    // Simulate trojan-like behavior
    const trojanFunction = () => {
      // Show hidden malicious UI after a delay
      setTimeout(() => {
        setHidden(false);
      }, 5000);
    };

    // Call the trojan function
    trojanFunction();
  }, []);

  return (
    <div>
      {hidden ? (
        <div style={{ display: 'none' }}>
          {/* Insert hidden malicious UI elements here */}
          <p>Do not click anything!</p>
          <button onClick={() => alert('You have been hacked!')}>Click here for free stuff</button>
        </div>
      ) : (
        <div>
          {/* Insert benign-looking UI elements here */}
          <p>Hello World!</p>
        </div>
      )}
    </div>
  );
};

export default MaliciousComponent;

```
