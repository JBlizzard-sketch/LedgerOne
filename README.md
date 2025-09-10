
     # LedgerOne Prototype

     LedgerOne is a financial management prototype for Kenyan businesses, supporting invoice processing, payroll, accounting, and AI-driven automation. Built with FastAPI and Streamlit, it includes Kenyan-specific features (KRA-compliant VAT, PAYE, NSSF, SHA, M-Pesa integration).

     ## Features
     - **Ingestion**: Upload CSV, XLSX, PDF, images; normalize to JSON/CSV (\`cell_02\`, \`cell_03\`).
     - **AI Services**: Vendor normalization, category classification, anomaly detection (\`cell_04\`).
     - **Accounting**: AP, AR, GL with double-entry bookkeeping (\`cell_05\`).
     - **Payroll**: Calculate PAYE, NSSF, SHA, Housing Levy; generate payslips (\`cell_06\`).
     - **Workflow & RBAC**: Role-based approvals (CEO, CFO, APClerk, etc.) (\`cell_07\`).
     - **Admin Console**: Manage tenants, roles, connectors via Streamlit UI (\`cell_08\`).
     - **Connectors**: M-Pesa, bank CSV, OCR with fallbacks (\`cell_09\`).
     - **Demo Data**: 3 tenants (manufacturing, service, retail) with realistic data (\`cell_10\`).

     ## Setup
     1. **Clone Repository**:
        \`\`\`bash
        git clone <repository_url>
        cd ledgerone_prototype
        \`\`\`

     2. **Install Dependencies**:
        \`\`\`bash
        pip install -r requirements.txt
        \`\`\`

     3. **Set Environment Variables**:
        Create \`.env\` in the root directory:
        \`\`\`
        SECRET_KEY=demo-secret-1234567890
        DB_URL=sqlite:///data/ledgerone.db
        LOG_LEVEL=INFO
        ENVIRONMENT=development
        MPESA_KEY=<your_mpesa_key>  # Optional
        LLM_API_KEY=<your_llm_key>  # Optional
        OCR_API_KEY=<your_ocr_key>  # Optional
        \`\`\`

     4. **Seed Demo Data**:
        \`\`\`bash
        python -m ledgerone_prototype.cell_10_faker_tests_deploy
        \`\`\`
        Demo credentials in \`data/DEMO_ACCOUNTS.md\`.

     5. **Run Application**:
        \`\`\`bash
        streamlit run run_app.py
        \`\`\`
        Access UI at \`http://localhost:8501\`. API at \`http://localhost:8000\`.

     6. **Run Tests**:
        \`\`\`bash
        ./run_tests_and_fix.sh
        \`\`\`

     7. **Deploy with Docker**:
        \`\`\`bash
        docker build -t ledgerone .
        docker run -p 8501:8501 ledgerone
        \`\`\`

     ## Usage
     - **Login**: Use credentials from \`data/DEMO_ACCOUNTS.md\` (e.g., \`superadmin/Super123!\`).
     - **Upload Files**: Upload invoices, payroll, or bank statements via UI or \`/ingest\` API.
     - **Admin Console**: Manage roles, thresholds, connectors (super admin: impersonation, retrain).
     - **View Reports**: Access ledger entries, payslips, and trial balances (role-based).

     ## Project Structure
     - \`ledgerone_prototype/\`: Python package with 10 cells.
     - \`data/\`: Stores raw, canonical, audit, demo, and payslip data.
     - \`requirements.txt\`: Dependencies.
     - \`run_app.py\`: Main entrypoint.
     - \`Dockerfile\`: Container setup.
     - \`run_tests_and_fix.sh\`: Test runner with auto-fix.

     ## Notes
     - Built for Kenyan businesses (KRA, NSSF, SHA compliance, 2025 rates).
     - Extensible: Add connectors, roles, or DB migrations.
     - Audit logs in \`data/audit/{tenant}/\`.
     - Demo data seeded for 3 tenants (manufacturing, service, retail).

     ## License
     MIT License. See \`LICENSE\` for details.
     EOF
     ```

3. **Verify Files**:
   - After creating the files, check they exist in your project directory:
     ```bash
     ls requirements.txt README.md
     ```
   - Open `requirements.txt` to confirm it lists all 18 dependencies.
   - Open `README.md` to verify setup instructions and project details.

