

### **Step-by-Step Solution: Changing the Execution Policy**

You'll need to open PowerShell with administrator privileges to change this setting.

#### **Step 1: Open PowerShell as Administrator**

1.  Click on the Windows **Start** button.
2.  Type "PowerShell".
3.  Right-click on "Windows PowerShell" in the search results.
4.  Select "Run as administrator".
5.  If prompted by User Account Control (UAC), click "Yes".

#### **Step 2: Check Your Current Execution Policy (Optional but Recommended)**

In the Administrator PowerShell window, run this command to see your current policy:

```powershell
Get-ExecutionPolicy
```
You will likely see `Restricted`.

#### **Step 3: Set the Execution Policy to `RemoteSigned`**

Now, run the following command to change the policy. This command is very common for developers.

```powershell
Set-ExecutionPolicy RemoteSigned
```

You will be asked to confirm the change. Type `Y` and press Enter.

#### **Step 4: Verify the Policy Change (Optional)**

You can run `Get-ExecutionPolicy` again to confirm it now shows `RemoteSigned`.

#### **Step 5: Activate Your Virtual Environment**

Now that the execution policy allows scripts to run, you can go back to your regular (non-administrator) command prompt or PowerShell window where your project is located and try activating your `venv` again.

**Make sure you are in your `agent_researcher` project directory.**

```bash
.\venv\Scripts\activate
```

This time, it should activate successfully, and you'll see `(venv)` at the beginning of your prompt.

---

### **Important Considerations**

*   **Security:** Setting `RemoteSigned` allows local scripts to run. While generally safe for developers, always be cautious about running scripts from untrusted sources, especially those downloaded from the internet.
*   **Reverting (Optional):** If you are particularly security-conscious and only want to enable this temporarily, you can change the policy back to `Restricted` after you've activated your virtual environment. However, you'll need to do this again every time you open a new PowerShell window and want to activate your `venv`. For most developers, leaving it at `RemoteSigned` is fine.
    ```powershell
    # To revert back to Restricted (Run as Administrator)
    Set-ExecutionPolicy Restricted
    ```

You've successfully navigated another common Windows Python development pitfall! You're now ready to install your `requirements.txt` and dive into building your CrewAI agent.