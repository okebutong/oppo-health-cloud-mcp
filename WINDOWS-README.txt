OPPO Health Cloud MCP for Windows

Files
- oppo-health-cloud-mcp.exe: MCP stdio server
- oppo-health-login.exe: interactive OPPO account login utility

First-time setup
1. Put both EXE files in a folder that you control, for example:
   C:\\OPPO-Health-MCP
2. Open PowerShell in that folder.
3. Run:
   .\\oppo-health-login.exe login
4. Follow the prompts. The login utility writes auth.json in the same folder.
   Keep auth.json private. It contains account credentials. Never upload it to GitHub,
   send it to anyone, or include it in screenshots or logs.
5. Confirm that curl.exe is available:
   where.exe curl.exe
   Windows 10/11 normally includes curl.exe. The server and login utility invoke
   curl.exe for OPPO cloud requests.

MCP client configuration
Use the full path to oppo-health-cloud-mcp.exe as the MCP server command.
Example:
{
  "mcpServers": {
    "oppo-health-cloud": {
      "command": "C:\\OPPO-Health-MCP\\oppo-health-cloud-mcp.exe"
    }
  }
}

Important
- The server uses stdio. Keep console mode enabled and do not launch it by double-clicking.
- auth.json and cloud_cache.db are created beside the EXE files.
- Keep the EXE files in a writable folder. Do not put them under Program Files.
- cloud_cache.db contains personal health data. Protect it like other private records.
- This build is for Windows x64. It does not install Python on your PC.
- curl.exe must be available on PATH. It is not bundled in the EXE.
- The login flow may request SMS verification and, for some accounts, secondary verification.
- If an EXE is blocked by Windows SmartScreen, verify that it came from your own GitHub Actions artifact before allowing it to run.
