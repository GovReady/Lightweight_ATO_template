id: ssp_v1_oscal_json
format: json
title: SSP v1 (OSCAL/JSON)
...

  { "system-security-plan" : 
    { "uuid" : "2fa78e07-74ef-4cd6-8124-bc0050c0c4df",
      "metadata" : 
      { "title" : "{{project.system_info.system_name}}",
        "published" : "2020-07-01T00:00:00.00-04:00",
        "last-modified" : "2020-07-01T00:00:00.00-04:00",
        "version" : "0.0",
        "oscal-version" : "1.0-Milestone3",
        "new-control-stuff": {
          "%for": "control in system.root_element.selected_controls_oscal_ctl_ids",
          "%loop": {
            "%if": "control.lower() in control_catalog",
            "%then":  {
              "uuid": "{{ system.control_implementation_as_dict[control]['elementcontrol_uuid'] }}",
              "control-id": "{{ control.lower() }}",
              "by-component": {
                "%for": "smt in system.control_implementation_as_dict[control]['control_impl_smts']",
                "%loop": {
                  "key": "{{ smt.producer_element.uuid }}", 
                  "value": { "uuid" : "{{ smt.uuid }}",
                    "component-name": "{{ smt.producer_element.name|safe }}",
                    "description" : "{{ smt.body|safe }}"
                  }
                }
              }
            }
          }
        },
        "revision-history" : 
        [ 
          { "published" : "2019-06-01T00:00:00.00-04:00",
            "version" : "1.0",
            "oscal-version" : "1.0-Milestone3",
            "properties" : 
            [ 
              { "name" : "party-uuid",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "6b286b5d-8f07-4fa7-8847-1dd0d88f73fb" } ],
            "remarks" : "Initial publication." },
          
          { "published" : "2020-06-01T00:00:00.00-04:00",
            "version" : "2.0",
            "oscal-version" : "1.0-Milestone3",
            "properties" : 
            [ 
              { "name" : "party-id",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "csp" } ],
            "remarks" : "Updated for annual assessment." } ],
        "properties" : 
        [ 
          { "name" : "marking",
            "value" : "Controlled Unclassified Information" } ],
        "roles" : 
        [ 
          { "id" : "prepared-by",
            "title" : "Prepared By",
            "desc" : "The organization that prepared this SSP. If developed in-house, this is the CSP itself." },
          
          { "id" : "prepared-for",
            "title" : "Prepared For",
            "desc" : "The organization for which this SSP was prepared. Typically the CSP." },
          
          { "id" : "content-approver",
            "title" : "System Security Plan Approval",
            "desc" : "The individual or individuals accountable for the accuracy of this SSP." },
          
          { "id" : "cloud-service-provider",
            "title" : "Cloud Service Provider",
            "short-name" : "CSP" },
          
          { "id" : "system-owner",
            "title" : "Information System Owner",
            "desc" : "The individual within the CSP who is ultimately accountable for everything related to this system." },
          
          { "id" : "authorizing-official",
            "title" : "Authorizing Official",
            "desc" : "The individual or individuals who must grant this system an authorization to operate." },
          
          { "id" : "authorizing-official-poc",
            "title" : "Authorizing Official's Point of Contact",
            "desc" : "The individual representing the authorizing official." },
          
          { "id" : "system-poc-management",
            "title" : "Information System Management Point of Contact (POC)",
            "desc" : "The highest level manager who responsible for system operation on behalf of the System Owner." },
          
          { "id" : "system-poc-technical",
            "title" : "Information System Technical Point of Contact",
            "desc" : "The individual or individuals leading the technical operation of the system." },
          
          { "id" : "system-poc-other",
            "title" : "General Point of Contact (POC)",
            "desc" : "A general point of contact for the system, designated by the system owner." },
          
          { "id" : "information-system-security-officer",
            "title" : "System Information System Security Officer (or Equivalent)",
            "desc" : "The individual accountable for the security posture of the system on behalf of the system owner." },
          
          { "id" : "privacy-poc",
            "title" : "Privacy Official's Point of Contact",
            "desc" : "The individual responsible for the privacy threshold analysis and if necessary the privacy impact assessment." },
          
          { "id" : "asset-owner",
            "title" : "Owner of an inventory item within the system." },
          
          { "id" : "asset-administrator",
            "title" : "Administrative responsibility an inventory item within the system." },
          
          { "id" : "isa-poc-local",
            "title" : "ICA POC (Local)",
            "desc" : "The point of contact for an interconnection on behalf of this system.",
            "remarks" : "Remove this role if there are no ICAs." },
          
          { "id" : "isa-poc-remote",
            "title" : "ICA POC (Remote)",
            "desc" : "The point of contact for an interconnection on behalf of this external system to which this system connects.",
            "remarks" : "Remove this role if there are no ICAs." },
          
          { "id" : "isa-authorizing-official-local",
            "title" : "ICA Signatory (Local)",
            "desc" : "Responsible for signing an interconnection security agreement on behalf of this system.",
            "remarks" : "Remove this role if there are no ICAs." },
          
          { "id" : "isa-authorizing-official-remote",
            "title" : "ICA Signatory (Remote)",
            "desc" : "Responsible for signing an interconnection security agreement on behalf of the external system to which this system connects.",
            "remarks" : "Remove this role if there are no ICAs." },
          
          { "id" : "consultant",
            "title" : "Consultant",
            "desc" : "Any consultants involved with developing or maintaining this content." },
          
          { "id" : "admin-unix",
            "title" : "[SAMPLE]Unix Administrator",
            "desc" : "This is a sample role." },
          
          { "id" : "admin-client",
            "title" : "[SAMPLE]Client Administrator",
            "desc" : "This is a sample role." },
          
          { "id" : "program-director",
            "title" : "[SAMPLE]Program Director",
            "desc" : "This is a sample role." },
          
          { "id" : "fedramp-pmo",
            "title" : "Federal Risk and Authorization Management Program (FedRAMP) Program Management Office (PMO)",
            "short-name" : "FedRAMP PMO" },
          
          { "id" : "fedramp-jab",
            "title" : "Federal Risk and Authorization Management Program (FedRAMP) Joint Authorization Board (JAB)",
            "short-name" : "FedRAMP JAB" } ],
        "locations" : 
        [ 
          { "uuid" : "27b78960-59ef-4619-82b0-ae20b9c709ac",
            "title" : "CSP HQ",
            "address" : 
            { "type" : "work",
              "postal-address" : 
              [ "Suite 0000",
                "1234 Some Street" ],
              "city" : "Haven",
              "state" : "ME",
              "postal-code" : "00000" },
            "remarks" : "There must be one location identifying the CSP's primary business address, such as the CSP's HQ, or the address of the system owner's primary business location." },
          
          { "uuid" : "16adcc8d-65d8-4583-80d3-9cf007744fec",
            "title" : "Primary Data Center",
            "address" : 
            { "postal-address" : 
              [ "2222 Main Street" ],
              "city" : "Anywhere",
              "state" : "--",
              "postal-code" : "00000-0000" },
            "properties" : 
            [ 
              { "name" : "conformity",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "data-center" },
              
              { "name" : "conformity",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "primary-data-center" } ],
            "remarks" : "There must be one location for each data center.\\n\\nThere must be at least two data centers.\\n\\nFor a data center, briefly summarize the components at this location.\\n\\nAll data centers must have a conformity tag of \\\"data-center\\\".\\n\\nA primary data center must also have a conformity tag of \\\"primary-data-center\\\"." },
          
          { "uuid" : "ad321514-7b9f-4374-8409-efb18eea6e5d",
            "title" : "Secondary Data Center",
            "address" : 
            { "postal-address" : 
              [ "3333 Small Road" ],
              "city" : "Anywhere",
              "state" : "--",
              "postal-code" : "00000-0000" },
            "properties" : 
            [ 
              { "name" : "conformity",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "data-center" },
              
              { "name" : "conformity",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "alternate-data-center" } ],
            "remarks" : "There must be one location for each data center.\\n\\nThere must be at least two data centers.\\n\\nFor a data center, briefly summarize the components at this location.\\n\\nAll data centers must have a conformity tag of \\\"data-center\\\"\\n\\nAn alternate or backup data center must also have a conformity tag of \\\"alternate-data-center\\\"." } ],
        "parties" : 
        [ 
          { "uuid" : "6b286b5d-8f07-4fa7-8847-1dd0d88f73fb",
            "type" : "organization",
            "party-name" : "Cloud Service Provider (CSP) Name",
            "short-name" : "CSP Acronym\/Short Name",
            "location-uuids" : 
            [ "27b78960-59ef-4619-82b0-ae20b9c709ac" ],
            "remarks" : "Replace sample CSP information." },
          
          { "uuid" : "77e0e2c8-2560-4fe9-ac78-c3ff4ffc9f6d",
            "type" : "organization",
            "party-name" : "Federal Risk and Authorization Management Program: Program Management Office",
            "short-name" : "FedRAMP PMO",
            "links" : 
            [ 
              { "href" : "https:\/\/fedramp.gov",
                "text" : "" } ],
            "addresses" : 
            [ 
              { "type" : "work",
                "postal-address" : 
                [ "1800 F St. NW",
                  "" ],
                "city" : "Washington",
                "state" : "DC",
                "postal-code" : "",
                "country" : "US" } ],
            "email-addresses" : 
            [ "info@fedramp.gov" ],
            "remarks" : "This party entry must be present in a FedRAMP SSP.\\n\\nThe uuid may be different; however, the uuid must be associated with the \\\"fedramp-pmo\\\" role in the responsible-party assemblies." },
          
          { "uuid" : "49017ec3-9f51-4dbd-9253-858c2b1295fd",
            "type" : "organization",
            "party-name" : "Federal Risk and Authorization Management Program: Joint Authorization Board",
            "short-name" : "FedRAMP JAB",
            "remarks" : "This party entry must be present in a FedRAMP SSP.\\n\\nThe uuid may be different; however, the uuid must be associated with the \\\"fedramp-jab\\\" role in the responsible-party assemblies." },
          
          { "uuid" : "78992555-4a99-4eaa-868c-f2c249679dd3",
            "type" : "organization",
            "party-name" : "External Organization",
            "short-name" : "External",
            "remarks" : "Generic placeholder for any external organization." },
          
          { "uuid" : "f595397b-cbe4-4a87-8c86-9bff91c4e7fd",
            "type" : "organization",
            "party-name" : "Agency Name",
            "short-name" : "A.N.",
            "remarks" : "Generic placeholder for an authorizing agency." },
          
          { "uuid" : "8e3d39da-4851-4d2a-adb5-4b5585ded952",
            "type" : "organization",
            "party-name" : "Name of Consulting Org",
            "short-name" : "NOCO",
            "links" : 
            [ 
              { "href" : "https:\/\/consulting.sample",
                "text" : "" } ],
            "addresses" : 
            [ 
              { "type" : "work",
                "postal-address" : 
                [ "3333 Corporate Way" ],
                "city" : "Washington",
                "state" : "DC",
                "postal-code" : "",
                "country" : "US" } ],
            "email-addresses" : 
            [ "poc@consulting.sample" ] },
          
          { "uuid" : "80361ec4-bfce-4b5c-85c8-313d6ebd220b",
            "type" : "organization",
            "party-name" : "[SAMPLE]Remote System Org Name" },
          
          { "uuid" : "09ad840f-aa79-43aa-9f22-25182c2ab11b",
            "type" : "person",
            "party-name" : "[SAMPLE]ICA POC's Name",
            "properties" : 
            [ 
              { "name" : "title",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "Individual's Title" } ],
            "email-addresses" : 
            [ "person@ica.org.example" ],
            "telephone-numbers" : 
            [ 
              { "number" : "202-555-1212" } ],
            "member-of-organizations" : 
            [ "80361ec4-bfce-4b5c-85c8-313d6ebd220b" ] },
          
          { "uuid" : "f0bc13a4-3303-47dd-80d3-380e159c8362",
            "type" : "organization",
            "party-name" : "[SAMPLE]Example IaaS Provider",
            "short-name" : "E.I.P.",
            "remarks" : "Underlying service provider. Leveraged Authorization." },
          
          { "uuid" : "3360e343-9860-4bda-9dfc-ff427c3dfab6",
            "type" : "person",
            "party-name" : "[SAMPLE]Person Name 1",
            "properties" : 
            [ 
              { "name" : "title",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "Individual's Title" } ],
            "addresses" : 
            [ 
              { "postal-address" : 
                [ "Mailstop A-1" ] } ],
            "email-addresses" : 
            [ "name@org.domain" ],
            "telephone-numbers" : 
            [ 
              { "number" : "202-000-0001" } ],
            "member-of-organizations" : 
            [ "6b286b5d-8f07-4fa7-8847-1dd0d88f73fb" ],
            "location-uuids" : 
            [ "27b78960-59ef-4619-82b0-ae20b9c709ac" ] },
          
          { "uuid" : "36b8d6c0-3b25-42cc-b529-cf4066145cdd",
            "type" : "person",
            "party-name" : "[SAMPLE]Person Name 2",
            "properties" : 
            [ 
              { "name" : "title",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "Individual's Title" } ],
            "addresses" : 
            [ 
              { "type" : "work",
                "postal-address" : 
                [ "Address Line" ],
                "city" : "City",
                "state" : "ST",
                "postal-code" : "00000",
                "country" : "US" } ],
            "email-addresses" : 
            [ "name@org.domain" ],
            "telephone-numbers" : 
            [ 
              { "number" : "202-000-0002" } ],
            "member-of-organizations" : 
            [ "6b286b5d-8f07-4fa7-8847-1dd0d88f73fb" ] },
          
          { "uuid" : "0cec09d9-20c6-470b-9ffc-85763375880b",
            "type" : "person",
            "party-name" : "[SAMPLE]Person Name 3",
            "properties" : 
            [ 
              { "name" : "title",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "Individual's Title" } ],
            "addresses" : 
            [ 
              { "type" : "work",
                "postal-address" : 
                [ "Address Line" ],
                "city" : "City",
                "state" : "ST",
                "postal-code" : "00000",
                "country" : "US" } ],
            "email-addresses" : 
            [ "name@org.domain" ],
            "telephone-numbers" : 
            [ 
              { "number" : "202-000-0003" } ],
            "member-of-organizations" : 
            [ "6b286b5d-8f07-4fa7-8847-1dd0d88f73fb" ] },
          
          { "uuid" : "f75e21f6-43d8-46ab-890d-7f2eebc5a830",
            "type" : "person",
            "party-name" : "[SAMPLE]Person Name 4",
            "properties" : 
            [ 
              { "name" : "title",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "Individual's Title" } ],
            "addresses" : 
            [ 
              { "type" : "work",
                "postal-address" : 
                [ "Address Line" ],
                "city" : "City",
                "state" : "ST",
                "postal-code" : "00000",
                "country" : "US" } ],
            "email-addresses" : 
            [ "name@org.domain" ],
            "telephone-numbers" : 
            [ 
              { "number" : "202-000-0004" } ],
            "member-of-organizations" : 
            [ "6b286b5d-8f07-4fa7-8847-1dd0d88f73fb" ] },
          
          { "uuid" : "132953a9-640c-46f7-9de9-3fa15ec99361",
            "type" : "person",
            "party-name" : "[SAMPLE]Person Name 5",
            "properties" : 
            [ 
              { "name" : "title",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "Individual's Title" } ],
            "addresses" : 
            [ 
              { "type" : "work",
                "postal-address" : 
                [ "Address Line" ],
                "city" : "City",
                "state" : "ST",
                "postal-code" : "00000",
                "country" : "US" } ],
            "email-addresses" : 
            [ "name@org.domain" ],
            "telephone-numbers" : 
            [ 
              { "number" : "202-000-0005" } ],
            "member-of-organizations" : 
            [ "6b286b5d-8f07-4fa7-8847-1dd0d88f73fb" ] },
          
          { "uuid" : "4fded5fd-7a65-47ea-bd76-df57c46e27d1",
            "type" : "person",
            "party-name" : "[SAMPLE]Person Name 6",
            "properties" : 
            [ 
              { "name" : "title",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "Individual's Title" } ],
            "addresses" : 
            [ 
              { "type" : "work",
                "postal-address" : 
                [ "Address Line" ],
                "city" : "City",
                "state" : "ST",
                "postal-code" : "00000",
                "country" : "US" } ],
            "email-addresses" : 
            [ "name@org.domain" ],
            "telephone-numbers" : 
            [ 
              { "number" : "202-000-0006" } ],
            "member-of-organizations" : 
            [ "78992555-4a99-4eaa-868c-f2c249679dd3" ] },
          
          { "uuid" : "db234cb7-1776-425c-9ac4-b067c1723011",
            "type" : "person",
            "party-name" : "[SAMPLE]Person Name 7",
            "properties" : 
            [ 
              { "name" : "title",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "Individual's Title" } ],
            "addresses" : 
            [ 
              { "type" : "work",
                "postal-address" : 
                [ "Address Line" ],
                "city" : "City",
                "state" : "ST",
                "postal-code" : "00000",
                "country" : "US" } ],
            "email-addresses" : 
            [ "name@org.domain" ],
            "telephone-numbers" : 
            [ 
              { "number" : "202-000-0007" } ],
            "member-of-organizations" : 
            [ "6b286b5d-8f07-4fa7-8847-1dd0d88f73fb" ] },
          
          { "uuid" : "b306f5af-b93a-4a7f-a2b2-37a44fc92a79",
            "type" : "organization",
            "party-name" : "[SAMPLE] IT Department" },
          
          { "uuid" : "59cdc953-5902-4fa4-a878-f3163854624c",
            "type" : "organization",
            "party-name" : "[SAMPLE]Security Team" } ],
        "responsible-parties" : 
        { "cloud-service-provider" : 
          { "party-uuids" : 
            [ "6b286b5d-8f07-4fa7-8847-1dd0d88f73fb" ],
            "remarks" : "Exactly one" },
          "prepared-by" : 
          { "party-uuids" : 
            [ "3360e343-9860-4bda-9dfc-ff427c3dfab6" ],
            "remarks" : "Exactly one" },
          "prepared-for" : 
          { "party-uuids" : 
            [ "6b286b5d-8f07-4fa7-8847-1dd0d88f73fb" ] },
          "content-approver" : 
          { "party-uuids" : 
            [ "3360e343-9860-4bda-9dfc-ff427c3dfab6",
              "36b8d6c0-3b25-42cc-b529-cf4066145cdd" ],
            "remarks" : "One or more" },
          "system-owner" : 
          { "party-uuids" : 
            [ "3360e343-9860-4bda-9dfc-ff427c3dfab6" ],
            "remarks" : "Exactly one" },
          "authorizing-official" : 
          { "party-uuids" : 
            [ "49017ec3-9f51-4dbd-9253-858c2b1295fd",
              "4fded5fd-7a65-47ea-bd76-df57c46e27d1" ],
            "remarks" : "One or more" },
          "system-poc-management" : 
          { "party-uuids" : 
            [ "0cec09d9-20c6-470b-9ffc-85763375880b" ],
            "remarks" : "Exactly one" },
          "system-poc-technical" : 
          { "party-uuids" : 
            [ "f75e21f6-43d8-46ab-890d-7f2eebc5a830" ],
            "remarks" : "Exactly one" },
          "information-system-security-officer" : 
          { "party-uuids" : 
            [ "132953a9-640c-46f7-9de9-3fa15ec99361" ],
            "remarks" : "Exactly one" },
          "authorizing-official-poc" : 
          { "party-uuids" : 
            [ "4fded5fd-7a65-47ea-bd76-df57c46e27d1" ],
            "remarks" : "Exactly one" },
          "privacy-poc" : 
          { "party-uuids" : 
            [ "db234cb7-1776-425c-9ac4-b067c1723011" ],
            "remarks" : "Exactly one" },
          "fedramp-pmo" : 
          { "party-uuids" : 
            [ "77e0e2c8-2560-4fe9-ac78-c3ff4ffc9f6d" ],
            "remarks" : "Exactly one" },
          "fedramp-jab" : 
          { "party-uuids" : 
            [ "49017ec3-9f51-4dbd-9253-858c2b1295fd" ],
            "remarks" : "Exactly one" } },
        "remarks" : "This OSCAL-based FedRAMP SSP Template can be used for the FedRAMP Low, Moderate, and\n            High baselines.\\n\\nGuidance for OSCAL-based FedRAMP Tailored content has not yet been developed." },
      "import-profile" : 
      { "href" : "#890170c3-d4fa-4d25-ab96-8e4bf7cc237c" },
      "system-characteristics" : 
      { "system-ids" : 
        [ 
          { "identifier-type" : "https:\/\/fedramp.gov",
            "id" : "F00000000" } ],
        "system-name" : "System's Full Name",
        "system-name-short" : "System's Short Name or Acronym",
        "description" : "Describe the purpose and functions of this system here.",
        "properties" : 
        [ 
          { "name" : "authorization-type",
            "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
            "value" : "fedramp-agency" },
          
          { "name" : "security-eauth-level",
            "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
            "class" : "security-eauth",
            "value" : "2" },
          
          { "name" : "identity-assurance-level",
            "value" : "2" },
          
          { "name" : "authenticator-assurance-level",
            "value" : "2" },
          
          { "name" : "federation-assurance-level",
            "value" : "2" } ],
        "annotations" : 
        [ 
          { "name" : "cloud-service-model",
            "value" : "saas",
            "remarks" : "Remarks are required if service model is \\\"other\\\". Optional otherwise." },
          
          { "name" : "cloud-deployment-model",
            "value" : "government-only-cloud",
            "remarks" : "Remarks are required if deployment model is \\\"hybrid-cloud\\\" or \\\"other\\\". Optional\n               otherwise." } ],
        "security-sensitivity-level" : "low",
        "system-information" : 
        { "properties" : 
          [ 
            { "name" : "privacy-sensitive",
              "value" : "yes" },
            
            { "name" : "pta-1",
              "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
              "class" : "pta",
              "value" : "yes" },
            
            { "name" : "pta-2",
              "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
              "class" : "pta",
              "value" : "yes" },
            
            { "name" : "pta-3",
              "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
              "class" : "pta",
              "value" : "yes" },
            
            { "name" : "pta-4",
              "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
              "class" : "pta",
              "value" : "no" },
            
            { "name" : "sorn-id",
              "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
              "class" : "pta",
              "value" : "[No SORN ID]" } ],
          "information-types" : 
          [ 
            { "uuid" : "06ecba4f-db96-4491-a3a2-7febfa227435",
              "title" : "Information Type Name",
              "description" : "A description of the information.",
              "information-type-ids" : 
              { "https:\/\/doi.org\/10.6028\/NIST.SP.800-60v2r1" : 
                { "id" : "C.2.4.1" } },
              "confidentiality-impact" : 
              { "base" : "fips-199-moderate",
                "selected" : "fips-199-moderate",
                "adjustment-justification" : "Required if the base and selected values do not match." },
              "integrity-impact" : 
              { "base" : "fips-199-moderate",
                "selected" : "fips-199-moderate",
                "adjustment-justification" : "Required if the base and selected values do not match." },
              "availability-impact" : 
              { "base" : "fips-199-moderate",
                "selected" : "fips-199-moderate",
                "adjustment-justification" : "Required if the base and selected values do not match." } } ] },
        "security-impact-level" : 
        { "security-objective-confidentiality" : "fips-199-moderate",
          "security-objective-integrity" : "fips-199-moderate",
          "security-objective-availability" : "fips-199-moderate" },
        "status" : 
        { "state" : "operational",
          "remarks" : "Remarks are required if status\/state is \\\"other\\\". Optional otherwise." },
        "authorization-boundary" : 
        { "description" : "A holistic, top-level explanation of the FedRAMP authorization boundary.",
          "diagrams" : 
          { "dbf46c27-52a9-49c4-beb6-b6399cd75497" : 
            { "description" : "A diagram-specific explanation.",
              "links" : 
              [ 
                { "href" : "#d2eb3c18-6754-4e3a-a933-03d289e3fad5",
                  "rel" : "diagram",
                  "text" : "" } ],
              "caption" : "Authorization Boundary Diagram" } } },
        "network-architecture" : 
        { "description" : "A holistic, top-level explanation of the network architecture.",
          "diagrams" : 
          { "e97c3395-433a-48c1-8cc7-dd1e1555941c" : 
            { "description" : "A diagram-specific explanation.",
              "links" : 
              [ 
                { "href" : "#61081e81-850b-43c1-bf43-1ecbddcb9e7f",
                  "rel" : "diagram",
                  "text" : "" } ],
              "caption" : "Network Diagram" } } },
        "data-flow" : 
        { "description" : "A holistic, top-level explanation of the system's data flows.",
          "diagrams" : 
          { "e3b98448-4219-46a5-b229-412423c566f3" : 
            { "description" : "A diagram-specific explanation.",
              "links" : 
              [ 
                { "href" : "#ac5d7535-f3b8-45d3-bf3b-735c82c64547",
                  "rel" : "diagram",
                  "text" : "" } ],
              "caption" : "Data Flow Diagram" } } } },
      "system-implementation" : 
      { "properties" : 
        [ 
          { "name" : "users-internal",
            "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
            "value" : "0" },
          
          { "name" : "users-external",
            "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
            "value" : "0" },
          
          { "name" : "users-internal-future",
            "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
            "value" : "0" },
          
          { "name" : "users-external-future",
            "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
            "value" : "0" } ],
        "leveraged-authorizations" : 
        [ 
          { "uuid" : "5a9c98ab-8e5e-433d-a7bd-515c07cd1497",
            "title" : "Name of Underlying System",
            "party-uuid" : "f0bc13a4-3303-47dd-80d3-380e159c8362",
            "date-authorized" : "2015-01-01",
            "remarks" : "The leveraged-authorizaton assembly is supposed to have a required uuid flag instead of an optional id flag. This will be fixed in the syntax shortly.\\n\\nUse one leveraged-authorization assembly for each underlying system. (In the legacy world, these may be general support systems." } ],
        "users" : 
        { "9cb0fab0-78bd-44ba-bcb8-3e9801cc952f" : 
          { "title" : "[SAMPLE]Unix System Administrator",
            "properties" : 
            [ 
              { "name" : "sensitivity",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "high" } ],
            "annotations" : 
            [ 
              { "name" : "privilege-level",
                "value" : "privileged" },
              
              { "name" : "type",
                "value" : "internal" } ],
            "role-ids" : 
            [ "admin-unix" ],
            "authorized-privileges" : 
            [ 
              { "title" : "Full administrative access (root)",
                "functions-performed" : 
                [ "Add\/remove users and hardware",
                  "install and configure software",
                  "OS updates, patches and hotfixes",
                  "perform backups" ] } ] },
          "16ec71e7-025c-43e4-9d3f-3acb485fac2e" : 
          { "title" : "[SAMPLE]Client Administrator",
            "properties" : 
            [ 
              { "name" : "sensitivity",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "moderate" } ],
            "annotations" : 
            [ 
              { "name" : "privilege-level",
                "value" : "non-privileged" },
              
              { "name" : "type",
                "value" : "external" } ],
            "role-ids" : 
            [ "external" ],
            "authorized-privileges" : 
            [ 
              { "title" : "Portal administration",
                "functions-performed" : 
                [ "Add\/remove client users",
                  "Create, modify and delete client applications" ] } ] },
          "ba7708c1-4041-48ab-9b7b-1ddb5e175fe0" : 
          { "title" : "[SAMPLE]Program Director",
            "properties" : 
            [ 
              { "name" : "sensitivity",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "limited" } ],
            "annotations" : 
            [ 
              { "name" : "privilege-level",
                "value" : "no-logical-access" },
              
              { "name" : "type",
                "value" : "internal" } ],
            "role-ids" : 
            [ "program-director" ],
            "authorized-privileges" : 
            [ 
              { "title" : "Administrative Access Approver",
                "functions-performed" : 
                [ "Approves access requests for administrative accounts." ] },
              
              { "title" : "Access Approver",
                "functions-performed" : 
                [ "Approves access requests for administrative accounts." ] } ] } },
        "components" : 
        { "60f92bcf-f353-4236-9803-2a5d417555f4" : 
          { "component-type" : "system",
            "title" : "This System",
            "description" : "The entire system as depicted in the system authorization boundary",
            "status" : 
            { "state" : "operational" } },
          "e82e6e07-0c62-417e-8a19-3744991b4c65" : 
          { "component-type" : "system",
            "title" : "Name of Leveraged System",
            "description" : "If the leveraged system owner provides a UUID for their system (such as in an OSCAL-based CRM), it should be used as the UUID for this component.",
            "properties" : 
            [ 
              { "name" : "leveraged-authorization-uuid",
                "value" : "5a9c98ab-8e5e-433d-a7bd-515c07cd1497" } ],
            "status" : 
            { "state" : "operational" } },
          "95beec7e-6f82-4aaa-8211-969cd7c1f1ab" : 
          { "component-type" : "validation",
            "title" : "[SAMPLE]Module Name",
            "description" : "[SAMPLE]FIPS 140-2 Validated Module",
            "properties" : 
            [ 
              { "name" : "cert-no",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "0000" } ],
            "links" : 
            [ 
              { "href" : "https:\/\/csrc.nist.gov\/projects\/cryptographic-module-validation-program\/Certificate\/0000",
                "text" : "" } ],
            "status" : 
            { "state" : "operational" } },
          "05ceb8df-52e7-49db-9719-891723f366bd" : 
          { "component-type" : "software",
            "title" : "[SAMPLE]Product Name",
            "description" : "FUNCTION: Describe typical component function.",
            "properties" : 
            [ 
              { "name" : "asset-type",
                "value" : "os" },
              
              { "name" : "scan-type",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "infrastructure" },
              
              { "name" : "vendor-name",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "Vendor Name" },
              
              { "name" : "model",
                "value" : "Model Number" },
              
              { "name" : "version",
                "value" : "Version Number" },
              
              { "name" : "patch-level",
                "value" : "Patch Level" },
              
              { "name" : "validation",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "fips-module-1" } ],
            "status" : 
            { "state" : "operational" },
            "responsible-roles" : 
            { "admin-unix" : 
              { "party-uuids" : 
                [ "3360e343-9860-4bda-9dfc-ff427c3dfab6" ] } },
            "remarks" : "COMMENTS: Provide other comments as needed." },
          "1541015b-6d19-42cb-a991-624cc082ed4d" : 
          { "component-type" : "hardware",
            "title" : "[SAMPLE]Product",
            "description" : "FUNCTION: Describe typical component function.",
            "properties" : 
            [ 
              { "name" : "asset-type",
                "value" : "database" },
              
              { "name" : "scan-type",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "infrastructure" },
              
              { "name" : "scan-type",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "database" },
              
              { "name" : "vendor-name",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "Vendor Name" },
              
              { "name" : "model",
                "value" : "Model Number" },
              
              { "name" : "version",
                "value" : "Version Number" } ],
            "status" : 
            { "state" : "operational" },
            "responsible-roles" : 
            { "asset-administrator" : 
              { "party-uuids" : 
                [ "b306f5af-b93a-4a7f-a2b2-37a44fc92a79" ] },
              "asset-owner" : 
              { "party-uuids" : 
                [ "36b8d6c0-3b25-42cc-b529-cf4066145cdd" ] } },
            "remarks" : "COMMENTS: Provide other comments as needed." },
          "6617f60b-8bac-422d-9939-94f43ddc0f7a" : 
          { "component-type" : "os",
            "title" : "OS Sample",
            "description" : "None",
            "properties" : 
            [ 
              { "name" : "asset-type",
                "value" : "os" },
              
              { "name" : "scan-type",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "infrastructure" } ],
            "annotations" : 
            [ 
              { "name" : "baseline-configuration-name",
                "value" : "Baseline Config. Name" },
              
              { "name" : "allows-authenticated-scan",
                "value" : "yes" } ],
            "status" : 
            { "state" : "operational" } },
          "120f1404-7c9f-4856-a247-63bd89d9e769" : 
          { "component-type" : "software",
            "title" : "Database Sample",
            "description" : "None",
            "properties" : 
            [ 
              { "name" : "asset-type",
                "value" : "database" },
              
              { "name" : "scan-type",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "database" } ],
            "annotations" : 
            [ 
              { "name" : "baseline-configuration-name",
                "value" : "Baseline Config. Name" },
              
              { "name" : "allows-authenticated-scan",
                "value" : "yes" } ],
            "status" : 
            { "state" : "operational" } },
          "8f230d84-2f9b-44a3-acdb-019566ab2554" : 
          { "component-type" : "software",
            "title" : "Appliance Sample",
            "description" : "None",
            "properties" : 
            [ 
              { "name" : "asset-type",
                "value" : "appliance" },
              
              { "name" : "scan-type",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "web" },
              
              { "name" : "login-url",
                "value" : "https:\/\/admin.offering.com\/login" } ],
            "annotations" : 
            [ 
              { "name" : "baseline-configuration-name",
                "value" : "Baseline Config. Name" },
              
              { "name" : "allows-authenticated-scan",
                "value" : "no",
                "remarks" : "Vendor appliance. No admin-level access." } ],
            "status" : 
            { "state" : "operational" } },
          "d5841417-de4c-4d84-ab3c-39dd1fd32a96" : 
          { "component-type" : "service",
            "title" : "[SAMPLE]Service Name",
            "description" : "Describe the service",
            "purpose" : "Describe the reason the service is needed.",
            "properties" : 
            [ 
              { "name" : "used-by",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "What uses this service?" },
              
              { "name" : "protocol",
                "value" : "" } ],
            "status" : 
            { "state" : "operational" },
            "protocols" : 
            [ 
              { "name" : "http",
                "port-ranges" : 
                [ 
                  { "start" : 80,
                    "end" : 80,
                    "transport" : "TCP" } ] },
              
              { "name" : "https",
                "port-ranges" : 
                [ 
                  { "start" : 443,
                    "end" : 443,
                    "transport" : "TCP" } ] } ],
            "remarks" : "Section 10.2, Table 10-1. Ports, Protocols and Services\\n\\n**SERVICES ARE NOW COMPONENTS WITH type='service'**" },
          "2812ef51-61e7-4505-afbb-da5a073a2a5b" : 
          { "component-type" : "interconnection",
            "title" : "[EXAMPLE]Authorized Connection Information System Name",
            "description" : "Briefly describe the interconnection.",
            "properties" : 
            [ 
              { "name" : "service-processor",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "[SAMPLE]Telco Name" },
              
              { "name" : "ipv4-address",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "class" : "local",
                "value" : "10.1.1.1" },
              
              { "name" : "ipv4-address",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "class" : "remote",
                "value" : "10.2.2.2" },
              
              { "name" : "direction",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "incoming-outgoing" },
              
              { "name" : "information",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "Describe the information being transmitted." },
              
              { "name" : "port",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "80" },
              
              { "name" : "circuit",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "1" } ],
            "annotations" : 
            [ 
              { "name" : "connection-security",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "ipsec",
                "remarks" : "If \\\"other\\\", remarks are required. Optional otherwise." } ],
            "links" : 
            [ 
              { "href" : "#9d6cf2b4-8e88-4040-a33c-7bc206553a1a",
                "rel" : "agreement",
                "text" : "" } ],
            "status" : 
            { "state" : "operational" },
            "responsible-roles" : 
            { "isa-poc-remote" : 
              { "party-uuids" : 
                [ "09ad840f-aa79-43aa-9f22-25182c2ab11b" ] },
              "isa-poc-local" : 
              { "party-uuids" : 
                [ "09ad840f-aa79-43aa-9f22-25182c2ab11b" ] },
              "isa-authorizing-official-remote" : 
              { "party-uuids" : 
                [ "09ad840f-aa79-43aa-9f22-25182c2ab11b" ] },
              "isa-authorizing-official-local" : 
              { "party-uuids" : 
                [ "09ad840f-aa79-43aa-9f22-25182c2ab11b" ] } },
            "remarks" : "Optional notes about this interconnection" } },
        "system-inventory" : 
        { "inventory-items" : 
          { "98e37f90-fbb5-4177-badb-9b55229cc183" : 
            { "asset-id" : "unique-asset-id",
              "description" : "Flat-File Example (No implemented-component).",
              "properties" : 
              [ 
                { "name" : "ipv4-address",
                  "value" : "10.1.1.1" },
                
                { "name" : "ipv6-address",
                  "value" : "0000:0000:0000:0000" },
                
                { "name" : "virtual",
                  "value" : "no" },
                
                { "name" : "public",
                  "value" : "no" },
                
                { "name" : "fqdn",
                  "value" : "dns.name" },
                
                { "name" : "uri",
                  "value" : "uniform.resource.identifier" },
                
                { "name" : "netbios-name",
                  "value" : "netbios-name" },
                
                { "name" : "mac-address",
                  "value" : "00:00:00:00:00:00" },
                
                { "name" : "software-name",
                  "value" : "software-name" },
                
                { "name" : "version",
                  "value" : "V 0.0.0" },
                
                { "name" : "asset-type",
                  "value" : "os" },
                
                { "name" : "vendor-name",
                  "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                  "value" : "Vendor Name" },
                
                { "name" : "model",
                  "value" : "Model Number" },
                
                { "name" : "patch-level",
                  "value" : "Patch-Level" },
                
                { "name" : "serial-number",
                  "value" : "Serial #" },
                
                { "name" : "asset-tag",
                  "value" : "Asset Tag" },
                
                { "name" : "vlan-id",
                  "value" : "VLAN Identifier" },
                
                { "name" : "network-id",
                  "value" : "Network Identifier" },
                
                { "name" : "scan-type",
                  "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                  "value" : "infrastructure" },
                
                { "name" : "scan-type",
                  "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                  "value" : "database" },
                
                { "name" : "validation",
                  "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                  "value" : "component-id" } ],
              "annotations" : 
              [ 
                { "name" : "allows-authenticated-scan",
                  "value" : "no",
                  "remarks" : "If no, explain why. If yes, omit remarks field." },
                
                { "name" : "baseline-configuration-name",
                  "value" : "Baseline Config. Name" },
                
                { "name" : "physical-location",
                  "value" : "Physical location of Asset" },
                
                { "name" : "is-scanned",
                  "value" : "yes",
                  "remarks" : "If no, explain why. If yes, omit remarks field." },
                
                { "name" : "function",
                  "value" : "Required brief, text-based description.",
                  "remarks" : "Optional, longer, formatted description." } ],
              "responsible-parties" : 
              { "asset-owner" : 
                { "party-uuids" : 
                  [ "db234cb7-1776-425c-9ac4-b067c1723011" ] },
                "asset-administrator" : 
                { "party-uuids" : 
                  [ "b306f5af-b93a-4a7f-a2b2-37a44fc92a79" ] } },
              "remarks" : "COMMENTS: Additional information about this item." },
            "c916d3c5-229e-4786-bf3f-4d71baa0e7a5" : 
            { "asset-id" : "unique-asset-ID",
              "description" : "Component Inventory Example",
              "properties" : 
              [ 
                { "name" : "ipv4-address",
                  "value" : "10.2.2.2" },
                
                { "name" : "ipv6-address",
                  "value" : "0000:0000:0000:0000" },
                
                { "name" : "mac-address",
                  "value" : "00:00:00:00:00:00" },
                
                { "name" : "virtual",
                  "value" : "no" },
                
                { "name" : "public",
                  "value" : "no" },
                
                { "name" : "fqdn",
                  "value" : "dns.name" },
                
                { "name" : "uri",
                  "value" : "uniform.resource.locator" },
                
                { "name" : "netbios-name",
                  "value" : "netbios-name" },
                
                { "name" : "patch-level",
                  "value" : "Patch-Level" } ],
              "annotations" : 
              [ 
                { "name" : "baseline-configuration-name",
                  "value" : "Baseline Configuration Name" },
                
                { "name" : "physical-location",
                  "value" : "Physical location of Asset" },
                
                { "name" : "scan-authenticated",
                  "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                  "value" : "no",
                  "remarks" : "If no, explain why. If yes, omit remark." },
                
                { "name" : "scan-latest",
                  "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                  "value" : "yes",
                  "remarks" : "If no, explain why. If yes, omit remark." } ],
              "responsible-parties" : 
              { "asset-owner" : 
                { "party-uuids" : 
                  [ "3360e343-9860-4bda-9dfc-ff427c3dfab6" ] },
                "asset-administrator" : 
                { "party-uuids" : 
                  [ "b306f5af-b93a-4a7f-a2b2-37a44fc92a79" ] } },
              "implemented-components" : 
              { "05ceb8df-52e7-49db-9719-891723f366bd" : 
                {  } },
              "remarks" : "COMMENTS: If needed, provide additional information about this inventory item." },
            "37c00d5a-ccf2-4112-a0ee-8460be8cff40" : 
            { "asset-id" : "unique-asset-id",
              "description" : "None.",
              "properties" : 
              [ 
                { "name" : "ipv4-address",
                  "value" : "10.3.3.3" } ],
              "annotations" : 
              [ 
                { "name" : "is-scanned",
                  "value" : "yes" } ],
              "implemented-components" : 
              { "1541015b-6d19-42cb-a991-624cc082ed4d" : 
                {  } } },
            "fb7a84fb-7e30-4f5b-9997-2ecd4d270bdd" : 
            { "asset-id" : "unique-asset-id",
              "description" : "None.",
              "properties" : 
              [ 
                { "name" : "ipv4-address",
                  "value" : "10.4.4.4" } ],
              "annotations" : 
              [ 
                { "name" : "is-scanned",
                  "value" : "yes" } ],
              "implemented-components" : 
              { "05ceb8df-52e7-49db-9719-891723f366bd" : 
                {  } } },
            "779d4e89-bba6-432c-b50d-d699fe534129" : 
            { "asset-id" : "unique-asset-id",
              "description" : "None.",
              "properties" : 
              [ 
                { "name" : "ipv4-address",
                  "value" : "10.5.5.5" } ],
              "annotations" : 
              [ 
                { "name" : "is-scanned",
                  "value" : "yes" } ],
              "implemented-components" : 
              { "8f230d84-2f9b-44a3-acdb-019566ab2554" : 
                {  } } },
            "20b207d5-5e77-4501-b02d-5d2a6e88db85" : 
            { "asset-id" : "unique-asset-id",
              "description" : "None.",
              "properties" : 
              [ 
                { "name" : "ipv4-address",
                  "value" : "10.6.6.6" } ],
              "annotations" : 
              [ 
                { "name" : "is-scanned",
                  "value" : "no",
                  "remarks" : "Asset wasn't running at time of scan." } ],
              "implemented-components" : 
              { "05ceb8df-52e7-49db-9719-891723f366bd" : 
                {  } } },
            "79b4f0d1-91ab-49e8-af28-045c12aa9272" : 
            { "asset-id" : "unique-asset-id",
              "description" : "None.",
              "properties" : 
              [ 
                { "name" : "ipv4-address",
                  "value" : "10.7.7.7" } ],
              "annotations" : 
              [ 
                { "name" : "is-scanned",
                  "value" : "yes" } ],
              "implemented-components" : 
              { "1541015b-6d19-42cb-a991-624cc082ed4d" : 
                {  } } },
            "b31b360d-b58b-4c7c-b344-68e17238d858" : 
            { "asset-id" : "unique-asset-id",
              "description" : "None.",
              "properties" : 
              [ 
                { "name" : "ipv4-address",
                  "value" : "10.8.8.8" } ],
              "annotations" : 
              [ 
                { "name" : "is-scanned",
                  "value" : "no",
                  "remarks" : "Asset wasn't running at time of scan." } ],
              "implemented-components" : 
              { "05ceb8df-52e7-49db-9719-891723f366bd" : 
                {  } } },
            "55b55b3d-3bd9-409a-bc87-3b9a2074bacd" : 
            { "asset-id" : "10.10.10.0",
              "description" : "IPv4 Production Subnet.",
              "properties" : 
              [ 
                { "name" : "ipv4-subnet",
                  "value" : "10.10.10.0\/24" } ],
              "annotations" : 
              [ 
                { "name" : "is-scanned",
                  "value" : "yes" } ] },
            "c0dbefa1-c8e8-4ca8-bd73-67cb7b1fa3f6" : 
            { "asset-id" : "10.10.20.0",
              "description" : "IPv4 Management Subnet.",
              "properties" : 
              [ 
                { "name" : "ipv4-subnet",
                  "value" : "10.10.20.0\/24" } ],
              "annotations" : 
              [ 
                { "name" : "is-scanned",
                  "value" : "yes" } ] } } } },
      "control-implementation" : 
      { "description" : "FedRAMP SSP Template Section 13\\n\\nThis description field is required by OSCAL. FedRAMP does not require any specific\n            information here.",
        "implemented-requirements" : 
        [ 
          { "uuid" : "eee8697a-bc39-45aa-accc-d3e534932efb",
            "control-id" : "ac-1",
            "properties" : 
            [ 
              { "name" : "planned-completion-date",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "2020-11-27Z" } ],
            "annotations" : 
            [ 
              { "name" : "implementation-status",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "planned",
                "remarks" : "Describe the plan to complete the implementation." },
              
              { "name" : "control-origination",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "sp-system" } ],
            "parameter-settings" : 
            { "ac-1_prm_1" : 
              { "value" : "[replace with list of personnel or roles]" },
              "ac-1_prm_2" : 
              { "value" : "[specify frequency]" },
              "ac-1_prm_3" : 
              { "value" : "[specify frequency]" } },
            "statements" : 
            { "ac-1_stmt.a" : 
              { "uuid" : "fb4d039a-dc4f-46f5-9c1f-f6343eaf69bc",
                "by-components" : 
                { "60f92bcf-f353-4236-9803-2a5d417555f4" : 
                  { "uuid" : "3f5612a4-cd1d-4c47-8cae-75d2eaa332cd",
                    "description" : "Describe how Part a is satisfied within the system." } },
                "remarks" : "The specified component is the system itself.\\n\\nAny control implementation response that can not be associated with another component is associated with the component representing the system." },
              "ac-1_stmt.a.1" : 
              { "uuid" : "0afdccce-b5ed-4127-ae19-cfbdd17d775e",
                "links" : 
                [ 
                  { "href" : "#090ab379-2089-4830-b9fd-26d0729e22e9",
                    "rel" : "policy",
                    "text" : "" } ],
                "remarks" : "This identifies a policy (attached in resources) that satisfies this control." },
              "ac-1_stmt.a.2" : 
              { "uuid" : "ffaf5e02-3055-40df-bbeb-3b94e834a43f",
                "links" : 
                [ 
                  { "href" : "#att-process-1",
                    "rel" : "process",
                    "text" : "" } ],
                "remarks" : "This identifies a process (attached in resources) that satisfies this control." },
              "ac-1_stmt.b.1" : 
              { "uuid" : "b46f97ec-55c1-4249-a9b9-3a228f1e3791",
                "description" : "Describe how Part b-1 is satisfied." },
              "ac-1_stmt.b.2" : 
              { "uuid" : "59c67969-3d5c-45f1-8e3e-1e642249633f",
                "description" : "Describe how Part b-2 is satisfied." } } },
          
          { "uuid" : "7a36cf53-156d-4d1f-9a8b-433f61cc57b7",
            "control-id" : "ac-2",
            "properties" : 
            [ 
              { "name" : "planned-completion-date",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "Completion Date" } ],
            "annotations" : 
            [ 
              { "name" : "implementation-status",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "planned",
                "remarks" : "Describe the plan to complete the implementation." },
              
              { "name" : "implementation-status",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "partial",
                "remarks" : "Describe the portion of the control that is not satisfied." },
              
              { "name" : "implementation-status",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "not-applicable",
                "remarks" : "Describe the justification for marking this control Not Applicable." },
              
              { "name" : "control-origination",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "sp-system" },
              
              { "name" : "control-origination",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "customer-configured",
                "remarks" : "Describe any customer-configured requirements for satisfying this control." } ],
            "responsible-roles" : 
            { "admin-unix" : 
              {  },
              "program-director" : 
              {  } },
            "parameter-settings" : 
            { "ac-2_prm_1" : 
              { "value" : "[SAMPLE]privileged, non-privileged" },
              "ac-2_prm_2" : 
              { "value" : "[SAMPLE]all" },
              "ac-2_prm_3" : 
              { "value" : "[SAMPLE]The Access Control Procedure" },
              "ac-2_prm_4" : 
              { "value" : "[SAMPLE]annually" } },
            "statements" : 
            { "ac-2_stmt.a" : 
              { "uuid" : "24a85abb-25ad-4686-850c-5c0e8ab69a0c",
                "description" : "Do not respond to this statement here. Respond within the `by-component` assembly below.",
                "by-components" : 
                { "60f92bcf-f353-4236-9803-2a5d417555f4" : 
                  { "uuid" : "8a72663c-28c7-41c2-8739-f1ee2d5761ac",
                    "description" : "For the portion of the control satisfied by this system or its owning organization, describe\n                        **how** the control is met.",
                    "annotations" : 
                    [ 
                      { "name" : "responsibility",
                        "value" : "customer",
                        "remarks" : "General customer responsibility description." } ],
                    "remarks" : "The component-uuid above points to the \\\"this system\\\" component.\\n\\nAny control response content that does not cleanly fit another system component is placed here. This includes customer responsibility content.\\n\\nThis can also be used to provide a summary, such as a holistic overview of how multiple components work together.\\n\\nWhile the \\\"this system\\\" component is not expclicity required within every `statement`, it will typically be present." },
                  "b7364f67-bf65-4df2-b756-4b9c6b1c4a52" : 
                  { "uuid" : "84de735f-ba37-4bb4-b784-79760f986a40",
                    "description" : "For the portion inherited from an underlying FedRAMP-authorized provider,\n                     describe **what** is inherited.",
                    "annotations" : 
                    [ 
                      { "name" : "responsibility",
                        "value" : "customer",
                        "remarks" : "Component-specific customer responsibility description." } ] },
                  "cae07d12-8566-443a-95de-7596b9cac953" : 
                  { "uuid" : "13db02bb-1f33-4f79-8711-ed47c2c3d337",
                    "description" : "For the portion of the control that must be configured by or provided by the\n                     customer, describe the customer responsibility here. This is what will appear\n                     in the Customer Responsibility Matrix." } } } } },
          
          { "uuid" : "c332a6f8-bbe6-4ee9-aaea-d89d251c68df",
            "control-id" : "at-1",
            "properties" : 
            [ 
              { "name" : "planned-completion-date",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "2020-11-27Z" } ],
            "annotations" : 
            [ 
              { "name" : "implementation-status",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "planned",
                "remarks" : "Describe the plan to complete the implementation." },
              
              { "name" : "control-origination",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "sp-system" } ],
            "responsible-roles" : 
            { "program-director" : 
              {  } },
            "parameter-settings" : 
            { "at-1_prm_1" : 
              { "value" : "[replace with list of personnel or roles]" },
              "at-1_prm_2" : 
              { "value" : "[specify frequency]" },
              "at-1_prm_3" : 
              { "value" : "[specify frequency]" } },
            "statements" : 
            { "at-1_stmt.a" : 
              { "uuid" : "ee5a11fb-9bae-4680-8f8c-575c85d47355",
                "description" : "Component-based Approach",
                "by-components" : 
                { "60f92bcf-f353-4236-9803-2a5d417555f4" : 
                  { "uuid" : "d3bdee1c-7d84-4ed4-8950-e13256edb7fa",
                    "description" : "Describe how Part a is satisfied." } } },
              "at-1_stmt.a.1" : 
              { "uuid" : "2e8ec7ce-c9c6-4f5f-9d50-3a3b9d3acf65",
                "links" : 
                [ 
                  { "href" : "#090ab379-2089-4830-b9fd-26d0729e22e9",
                    "rel" : "policy",
                    "text" : "" } ],
                "remarks" : "This identifies a policy (attached in resources) that satisfies this control." },
              "at-1_stmt.a.2" : 
              { "uuid" : "e7f9b618-c092-4b8b-b416-0ee477026726",
                "links" : 
                [ 
                  { "href" : "#att-process-1",
                    "rel" : "process",
                    "text" : "" } ],
                "remarks" : "This identifies a process (attached in resources) that satisfies this control." },
              "at-1_stmt.b.1" : 
              { "uuid" : "29192f0b-edb1-4820-b951-65ffdc64bb3e",
                "description" : "Ignore.",
                "by-components" : 
                { "60f92bcf-f353-4236-9803-2a5d417555f4" : 
                  { "uuid" : "5a5e5c3e-1108-47f1-a83f-05e0394219db",
                    "description" : "Describe how Part b-1 is satisfied." } } },
              "at-1_stmt.b.2" : 
              { "uuid" : "23a9bfa7-6e3f-4e00-a120-791b26a9157e",
                "description" : "Ignore.",
                "by-components" : 
                { "60f92bcf-f353-4236-9803-2a5d417555f4" : 
                  { "uuid" : "fcc63699-04ab-4b69-b7b9-a13bee6685b3",
                    "description" : "Describe how Part b-2 is satisfied." } } } } },
          
          { "uuid" : "381c8d0c-e6ec-41a9-9b16-01657226c70f",
            "control-id" : "au-1",
            "properties" : 
            [ 
              { "name" : "planned-completion-date",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "2020-11-27Z" } ],
            "annotations" : 
            [ 
              { "name" : "implementation-status",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "planned",
                "remarks" : "Describe the plan to complete the implementation." },
              
              { "name" : "control-origination",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "sp-system" } ],
            "responsible-roles" : 
            { "program-director" : 
              {  } },
            "parameter-settings" : 
            { "au-1_prm_1" : 
              { "value" : "[replace with list of personnel or roles]" },
              "au-1_prm_2" : 
              { "value" : "[specify frequency]" },
              "au-1_prm_3" : 
              { "value" : "[specify frequency]" } },
            "statements" : 
            { "au-1_stmt.a" : 
              { "uuid" : "9a2bd937-226e-4aaf-8261-2cf0c2e3aa10",
                "description" : "Ignore.",
                "by-components" : 
                { "60f92bcf-f353-4236-9803-2a5d417555f4" : 
                  { "uuid" : "30042cb9-ff85-472f-b769-68bd7bb5bbd9",
                    "description" : "For the portion of the control satisfied by the service provider, describe\n                        **how** the control is met." } } },
              "au-1_stmt.b.1" : 
              { "uuid" : "d01f186f-a14f-4e22-b069-84a55e48a112",
                "description" : "Ignore.",
                "by-components" : 
                { "60f92bcf-f353-4236-9803-2a5d417555f4" : 
                  { "uuid" : "f41962c7-b53b-46f8-a84f-4aba25904bb8",
                    "description" : "For the portion of the control satisfied by the service provider, describe\n                        **how** the control is met." } } },
              "au-1_stmt.b.2" : 
              { "uuid" : "ea153acb-2bd0-41d9-8ebd-ba022d31230a",
                "description" : "Ignore.",
                "by-components" : 
                { "60f92bcf-f353-4236-9803-2a5d417555f4" : 
                  { "uuid" : "9ad59f0d-17a2-4f3f-af6a-a8529d692195",
                    "description" : "For the portion of the control satisfied by the service provider, describe\n                        **how** the control is met." } } } } },
          
          { "uuid" : "43e388d9-3854-44f6-8c6f-17a6d51ee6a2",
            "control-id" : "ca-1",
            "properties" : 
            [ 
              { "name" : "planned-completion-date",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "2020-11-27Z" } ],
            "annotations" : 
            [ 
              { "name" : "implementation-status",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "planned",
                "remarks" : "Describe the plan to complete the implementation." },
              
              { "name" : "control-origination",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "sp-system" } ],
            "responsible-roles" : 
            { "program-director" : 
              {  } },
            "parameter-settings" : 
            { "ca-1_prm_1" : 
              { "value" : "[replace with list of personnel or roles]" },
              "ca-1_prm_2" : 
              { "value" : "[specify frequency]" },
              "ca-1_prm_3" : 
              { "value" : "[specify frequency]" } },
            "statements" : 
            { "ca-1_stmt.a" : 
              { "uuid" : "e7bd0a7e-5f92-4769-8cd3-76ad2f663a5c",
                "description" : "Ignore.",
                "by-components" : 
                { "60f92bcf-f353-4236-9803-2a5d417555f4" : 
                  { "uuid" : "e5815f1d-ec94-4d98-8896-ec57e339bd7b",
                    "description" : "For the portion of the control satisfied by the service provider, describe\n                        **how** the control is met." } } },
              "ca-1_stmt.b.1" : 
              { "uuid" : "b2c3ec86-b976-4e5a-9dc3-4ac2d570765e",
                "description" : "Ignore.",
                "by-components" : 
                { "60f92bcf-f353-4236-9803-2a5d417555f4" : 
                  { "uuid" : "ca6b2bd5-3ddf-4167-a942-06e1955e49f8",
                    "description" : "For the portion of the control satisfied by the service provider, describe\n                        **how** the control is met." } } },
              "ca-1_stmt.b.2" : 
              { "uuid" : "e9474eb8-36d6-4eab-abeb-f9bd17e66b22",
                "description" : "Ignore.",
                "by-components" : 
                { "60f92bcf-f353-4236-9803-2a5d417555f4" : 
                  { "uuid" : "507b8b9d-2d40-4748-81c9-c5a13c8f8f05",
                    "description" : "For the portion of the control satisfied by the service provider, describe\n                        **how** the control is met." } } } } },
          
          { "uuid" : "c8e45d78-2afe-42ae-80e1-c1e2499a0346",
            "control-id" : "cm-1",
            "properties" : 
            [ 
              { "name" : "planned-completion-date",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "2020-11-27Z" } ],
            "annotations" : 
            [ 
              { "name" : "implementation-status",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "planned",
                "remarks" : "Describe the plan to complete the implementation." },
              
              { "name" : "control-origination",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "sp-system" } ],
            "responsible-roles" : 
            { "program-director" : 
              {  } },
            "parameter-settings" : 
            { "cm-1_prm_1" : 
              { "value" : "[replace with list of personnel or roles]" },
              "cm-1_prm_2" : 
              { "value" : "[specify frequency]" },
              "cm-1_prm_3" : 
              { "value" : "[specify frequency]" } },
            "statements" : 
            { "cm-1_stmt.a" : 
              { "uuid" : "52339583-19b6-4774-9213-50b9f42fe51f",
                "description" : "Ignore.",
                "by-components" : 
                { "60f92bcf-f353-4236-9803-2a5d417555f4" : 
                  { "uuid" : "2916ebd5-c45a-466e-b8e9-00dd15b0c94d",
                    "description" : "For the portion of the control satisfied by the service provider, describe\n                        **how** the control is met." } } },
              "cm-1_stmt.b.1" : 
              { "uuid" : "f9cc6f3f-c64f-4fae-9a32-f964ebdc8e74",
                "description" : "Ignore.",
                "by-components" : 
                { "60f92bcf-f353-4236-9803-2a5d417555f4" : 
                  { "uuid" : "678db1d2-a538-4986-ac94-63da312fe3f9",
                    "description" : "For the portion of the control satisfied by the service provider, describe\n                        **how** the control is met." } } },
              "cm-1_stmt.b.2" : 
              { "uuid" : "c548a71f-41d6-4e8c-b400-1764379348c4",
                "description" : "Ignore.",
                "by-components" : 
                { "60f92bcf-f353-4236-9803-2a5d417555f4" : 
                  { "uuid" : "a871cf91-04c7-4e03-9df6-80b3d5afc9bf",
                    "description" : "For the portion of the control satisfied by the service provider, describe\n                        **how** the control is met." } } } } },
          
          { "uuid" : "13af9343-73e7-4d71-b386-9a0844fa7e45",
            "control-id" : "cp-1",
            "properties" : 
            [ 
              { "name" : "planned-completion-date",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "2020-11-27Z" } ],
            "annotations" : 
            [ 
              { "name" : "implementation-status",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "planned",
                "remarks" : "Describe the plan to complete the implementation." },
              
              { "name" : "control-origination",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "sp-system" } ],
            "responsible-roles" : 
            { "program-director" : 
              {  } },
            "parameter-settings" : 
            { "cp-1_prm_1" : 
              { "value" : "[replace with list of personnel or roles]" },
              "cp-1_prm_2" : 
              { "value" : "[specify frequency]" },
              "cp-1_prm_3" : 
              { "value" : "[specify frequency]" } },
            "statements" : 
            { "cp-1_stmt.a" : 
              { "uuid" : "8bde1fa5-eb81-4a1b-9e6e-5827e176025a",
                "description" : "Ignore.",
                "by-components" : 
                { "60f92bcf-f353-4236-9803-2a5d417555f4" : 
                  { "uuid" : "157d7751-938c-441f-9299-02a339d98532",
                    "description" : "For the portion of the control satisfied by the service provider, describe\n                        **how** the control is met." } } },
              "cp-1_stmt.b.1" : 
              { "uuid" : "2fc9eec1-a49f-4cfa-9f7b-c702a1e21619",
                "description" : "Ignore.",
                "by-components" : 
                { "60f92bcf-f353-4236-9803-2a5d417555f4" : 
                  { "uuid" : "6358db78-bab1-4139-b512-f65d3e48248b",
                    "description" : "For the portion of the control satisfied by the service provider, describe\n                        **how** the control is met." } } },
              "cp-1_stmt.b.2" : 
              { "uuid" : "db5b3977-bd51-4505-b3e2-1597bbd4d930",
                "description" : "Ignore.",
                "by-components" : 
                { "60f92bcf-f353-4236-9803-2a5d417555f4" : 
                  { "uuid" : "3de33bbe-1a15-4d10-b35d-56fd85e24571",
                    "description" : "For the portion of the control satisfied by the service provider, describe\n                        **how** the control is met." } } } } },
          
          { "uuid" : "4050c933-3ecc-4a8d-8da7-391364685cbb",
            "control-id" : "ia-1",
            "properties" : 
            [ 
              { "name" : "planned-completion-date",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "2020-11-27Z" } ],
            "annotations" : 
            [ 
              { "name" : "implementation-status",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "planned",
                "remarks" : "Describe the plan to complete the implementation." },
              
              { "name" : "control-origination",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "sp-system" } ],
            "responsible-roles" : 
            { "program-director" : 
              {  } },
            "parameter-settings" : 
            { "ia-1_prm_1" : 
              { "value" : "[replace with list of personnel or roles]" },
              "ia-1_prm_2" : 
              { "value" : "[specify frequency]" },
              "ia-1_prm_3" : 
              { "value" : "[specify frequency]" } },
            "statements" : 
            { "ia-1_stmt.a" : 
              { "uuid" : "ba92e479-705f-47a4-a763-dfc098ba239d",
                "description" : "Ignore.",
                "by-components" : 
                { "60f92bcf-f353-4236-9803-2a5d417555f4" : 
                  { "uuid" : "5add335d-7375-49f0-843c-ac994e4d147b",
                    "description" : "For the portion of the control satisfied by the service provider, describe\n                        **how** the control is met." } } },
              "ia-1_stmt.b.1" : 
              { "uuid" : "dba8c469-5758-497e-9856-e472a2e08677",
                "description" : "Ignore.",
                "by-components" : 
                { "60f92bcf-f353-4236-9803-2a5d417555f4" : 
                  { "uuid" : "b04d86a0-b68c-41f0-9c0b-88a8daa457b7",
                    "description" : "For the portion of the control satisfied by the service provider, describe\n                        **how** the control is met." } } },
              "ia-1_stmt.b.2" : 
              { "uuid" : "b56e37b1-1f4c-479b-bfa1-a2773c2eebfd",
                "description" : "Ignore.",
                "by-components" : 
                { "60f92bcf-f353-4236-9803-2a5d417555f4" : 
                  { "uuid" : "c8fde380-9a41-404a-a88b-c20479a21618",
                    "description" : "For the portion of the control satisfied by the service provider, describe\n                        **how** the control is met." } } } } },
          
          { "uuid" : "229846dc-83cc-4ff2-a9ed-210490a343d9",
            "control-id" : "ir-1",
            "properties" : 
            [ 
              { "name" : "planned-completion-date",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "2020-11-27Z" } ],
            "annotations" : 
            [ 
              { "name" : "implementation-status",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "planned",
                "remarks" : "Describe the plan to complete the implementation." },
              
              { "name" : "control-origination",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "sp-system" } ],
            "responsible-roles" : 
            { "program-director" : 
              {  } },
            "parameter-settings" : 
            { "ir-1_prm_1" : 
              { "value" : "[replace with list of personnel or roles]" },
              "ir-1_prm_2" : 
              { "value" : "[specify frequency]" },
              "ir-1_prm_3" : 
              { "value" : "[specify frequency]" } },
            "statements" : 
            { "ir-1_stmt.a" : 
              { "uuid" : "7284efc2-d953-486c-ab8a-3caef6ce06c3",
                "description" : "Ignore.",
                "by-components" : 
                { "60f92bcf-f353-4236-9803-2a5d417555f4" : 
                  { "uuid" : "7b385445-5e7b-4656-98f1-0f1353aab59e",
                    "description" : "For the portion of the control satisfied by the service provider, describe\n                        **how** the control is met." } } },
              "ir-1_stmt.b.1" : 
              { "uuid" : "75c37e1a-6e8d-4ef0-99f4-c16f7995706c",
                "description" : "Ignore.",
                "by-components" : 
                { "60f92bcf-f353-4236-9803-2a5d417555f4" : 
                  { "uuid" : "e7ae4685-2e30-4e00-9ada-b00b5eaf5578",
                    "description" : "For the portion of the control satisfied by the service provider, describe\n                        **how** the control is met." } } },
              "ir-1_stmt.b.2" : 
              { "uuid" : "900591ec-2006-4622-bc87-59828d884d4f",
                "description" : "Ignore.",
                "by-components" : 
                { "60f92bcf-f353-4236-9803-2a5d417555f4" : 
                  { "uuid" : "f443c391-479d-492d-b7e9-55c9c2c107be",
                    "description" : "For the portion of the control satisfied by the service provider, describe\n                        **how** the control is met." } } } } },
          
          { "uuid" : "f0c6b63f-6b94-448f-bb16-db3d54b91734",
            "control-id" : "ma-1",
            "properties" : 
            [ 
              { "name" : "planned-completion-date",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "2020-11-27Z" } ],
            "annotations" : 
            [ 
              { "name" : "implementation-status",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "planned",
                "remarks" : "Describe the plan to complete the implementation." },
              
              { "name" : "control-origination",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "sp-system" } ],
            "responsible-roles" : 
            { "program-director" : 
              {  } },
            "parameter-settings" : 
            { "ma-1_prm_1" : 
              { "value" : "[replace with list of personnel or roles]" },
              "ma-1_prm_2" : 
              { "value" : "[specify frequency]" },
              "ma-1_prm_3" : 
              { "value" : "[specify frequency]" } },
            "statements" : 
            { "ma-1_stmt.a" : 
              { "uuid" : "d609e538-3976-418e-a368-58fc75cd03c0",
                "description" : "Ignore.",
                "by-components" : 
                { "60f92bcf-f353-4236-9803-2a5d417555f4" : 
                  { "uuid" : "93a9b046-63c4-4628-8547-39bc7d8df70c",
                    "description" : "For the portion of the control satisfied by the service provider, describe\n                        **how** the control is met." } } },
              "ma-1_stmt.b.1" : 
              { "uuid" : "df1a6dd8-9e18-4408-8783-cb30e0413f22",
                "description" : "Ignore.",
                "by-components" : 
                { "60f92bcf-f353-4236-9803-2a5d417555f4" : 
                  { "uuid" : "ad14f76a-a3eb-4349-8f6c-54cd99f1c040",
                    "description" : "For the portion of the control satisfied by the service provider, describe\n                        **how** the control is met." } } },
              "ma-1_stmt.b.2" : 
              { "uuid" : "f02f759d-7d4c-41f2-b153-f3cc1e157e39",
                "description" : "Ignore.",
                "by-components" : 
                { "60f92bcf-f353-4236-9803-2a5d417555f4" : 
                  { "uuid" : "32b337f6-eb61-4945-a139-4d2ae7737488",
                    "description" : "For the portion of the control satisfied by the service provider, describe\n                        **how** the control is met." } } } } },
          
          { "uuid" : "fa3a9747-3451-456a-aae9-9896e03a52c8",
            "control-id" : "mp-1",
            "properties" : 
            [ 
              { "name" : "planned-completion-date",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "2020-11-27Z" } ],
            "annotations" : 
            [ 
              { "name" : "implementation-status",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "planned",
                "remarks" : "Describe the plan to complete the implementation." },
              
              { "name" : "control-origination",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "sp-system" } ],
            "responsible-roles" : 
            { "program-director" : 
              {  } },
            "parameter-settings" : 
            { "mp-1_prm_1" : 
              { "value" : "[replace with list of personnel or roles]" },
              "mp-1_prm_2" : 
              { "value" : "[specify frequency]" },
              "mp-1_prm_3" : 
              { "value" : "[specify frequency]" } },
            "statements" : 
            { "mp-1_stmt.a" : 
              { "uuid" : "bab45ad3-65ee-43bc-9c3e-c3e4e2db8001",
                "description" : "Ignore.",
                "by-components" : 
                { "60f92bcf-f353-4236-9803-2a5d417555f4" : 
                  { "uuid" : "6668f521-4d5c-4317-868f-804878675bf2",
                    "description" : "For the portion of the control satisfied by the service provider, describe\n                        **how** the control is met." } } },
              "mp-1_stmt.b.1" : 
              { "uuid" : "ca35d4a5-ca73-4b3a-aa66-6c712c7a4a49",
                "description" : "Ignore.",
                "by-components" : 
                { "60f92bcf-f353-4236-9803-2a5d417555f4" : 
                  { "uuid" : "57e65240-5b41-40ee-89b1-f75d8fb259ad",
                    "description" : "For the portion of the control satisfied by the service provider, describe\n                        **how** the control is met." } } },
              "mp-1_stmt.b.2" : 
              { "uuid" : "0c5c6eda-9644-46f2-a29c-16fe4e248621",
                "description" : "Ignore.",
                "by-components" : 
                { "60f92bcf-f353-4236-9803-2a5d417555f4" : 
                  { "uuid" : "ea6c7fa7-ccbf-414c-8c6b-9c928e914b35",
                    "description" : "For the portion of the control satisfied by the service provider, describe\n                        **how** the control is met." } } } } },
          
          { "uuid" : "a85ff28e-517c-4455-8bd4-866103a2c94a",
            "control-id" : "pe-1",
            "properties" : 
            [ 
              { "name" : "planned-completion-date",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "2020-11-27Z" } ],
            "annotations" : 
            [ 
              { "name" : "implementation-status",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "planned",
                "remarks" : "Describe the plan to complete the implementation." },
              
              { "name" : "control-origination",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "sp-system" } ],
            "responsible-roles" : 
            { "program-director" : 
              {  } },
            "parameter-settings" : 
            { "pe-1_prm_1" : 
              { "value" : "[replace with list of personnel or roles]" },
              "pe-1_prm_2" : 
              { "value" : "[specify frequency]" },
              "pe-1_prm_3" : 
              { "value" : "[specify frequency]" } },
            "statements" : 
            { "pe-1_stmt.a" : 
              { "uuid" : "11fd3e46-4735-4986-91bc-747345fe608a",
                "description" : "Ignore.",
                "by-components" : 
                { "60f92bcf-f353-4236-9803-2a5d417555f4" : 
                  { "uuid" : "dceb4401-c1fd-41a7-9e07-8d82a8042e61",
                    "description" : "For the portion of the control satisfied by the service provider, describe\n                        **how** the control is met." } } },
              "pe-1_stmt.b.1" : 
              { "uuid" : "a37f91e2-190d-40f7-829c-39776c14c8b4",
                "description" : "Ignore.",
                "by-components" : 
                { "60f92bcf-f353-4236-9803-2a5d417555f4" : 
                  { "uuid" : "bbd2b372-b57d-4a3a-90c2-2189dd23664b",
                    "description" : "For the portion of the control satisfied by the service provider, describe\n                        **how** the control is met." } } },
              "pe-1_stmt.b.2" : 
              { "uuid" : "f3d57138-916c-4064-b2fc-aa8dd76849f8",
                "description" : "Ignore.",
                "by-components" : 
                { "60f92bcf-f353-4236-9803-2a5d417555f4" : 
                  { "uuid" : "f4a94538-220f-4f73-9487-73b72b68813e",
                    "description" : "For the portion of the control satisfied by the service provider, describe\n                        **how** the control is met." } } } } },
          
          { "uuid" : "97ba1f95-92a8-480b-a489-960661e4206b",
            "control-id" : "pl-1",
            "properties" : 
            [ 
              { "name" : "planned-completion-date",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "2020-11-27Z" } ],
            "annotations" : 
            [ 
              { "name" : "implementation-status",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "planned",
                "remarks" : "Describe the plan to complete the implementation." },
              
              { "name" : "control-origination",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "sp-system" } ],
            "responsible-roles" : 
            { "program-director" : 
              {  } },
            "parameter-settings" : 
            { "pl-1_prm_1" : 
              { "value" : "[replace with list of personnel or roles]" },
              "pl-1_prm_2" : 
              { "value" : "[specify frequency]" },
              "pl-1_prm_3" : 
              { "value" : "[specify frequency]" } },
            "statements" : 
            { "pl-1_stmt.a" : 
              { "uuid" : "ec7af577-ff22-46bf-ac0a-cf9d75c72ebb",
                "description" : "Ignore.",
                "by-components" : 
                { "60f92bcf-f353-4236-9803-2a5d417555f4" : 
                  { "uuid" : "679837fb-601e-4517-abe6-11ff6fc551b4",
                    "description" : "For the portion of the control satisfied by the service provider, describe\n                        **how** the control is met." } } },
              "pl-1_stmt.b.1" : 
              { "uuid" : "438f3e29-670a-49f2-8b9f-05d951318294",
                "description" : "Ignore.",
                "by-components" : 
                { "60f92bcf-f353-4236-9803-2a5d417555f4" : 
                  { "uuid" : "ddce2988-ce9b-4f15-a427-6f18e4ba1817",
                    "description" : "For the portion of the control satisfied by the service provider, describe\n                        **how** the control is met." } } },
              "pl-1_stmt.b.2" : 
              { "uuid" : "96a4d13c-bd2b-4038-96c5-0f923f404bbd",
                "description" : "Ignore.",
                "by-components" : 
                { "60f92bcf-f353-4236-9803-2a5d417555f4" : 
                  { "uuid" : "18d7c02e-f21b-4cd2-bf33-d27971ced47f",
                    "description" : "For the portion of the control satisfied by the service provider, describe\n                        **how** the control is met." } } } } },
          
          { "uuid" : "5e7498de-b540-4a28-b041-4381b023e98a",
            "control-id" : "ps-1",
            "properties" : 
            [ 
              { "name" : "planned-completion-date",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "2020-11-27Z" } ],
            "annotations" : 
            [ 
              { "name" : "implementation-status",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "planned",
                "remarks" : "Describe the plan to complete the implementation." },
              
              { "name" : "control-origination",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "sp-system" } ],
            "responsible-roles" : 
            { "program-director" : 
              {  } },
            "parameter-settings" : 
            { "ps-1_prm_1" : 
              { "value" : "[replace with list of personnel or roles]" },
              "ps-1_prm_2" : 
              { "value" : "[specify frequency]" },
              "ps-1_prm_3" : 
              { "value" : "[specify frequency]" } },
            "statements" : 
            { "ps-1_stmt.a" : 
              { "uuid" : "afe1703d-5e59-460b-b048-41b49699c5a1",
                "description" : "Ignore.",
                "by-components" : 
                { "60f92bcf-f353-4236-9803-2a5d417555f4" : 
                  { "uuid" : "7d6cafb2-b613-4807-ad61-4f0f649bd5ee",
                    "description" : "For the portion of the control satisfied by the service provider, describe\n                        **how** the control is met." } } },
              "ps-1_stmt.b.1" : 
              { "uuid" : "956c93e2-cf8f-482c-aaf7-91ab44c7cbd6",
                "description" : "Ignore.",
                "by-components" : 
                { "60f92bcf-f353-4236-9803-2a5d417555f4" : 
                  { "uuid" : "f4fbfbc2-1a94-456d-a713-9d547f18a0c7",
                    "description" : "For the portion of the control satisfied by the service provider, describe\n                        **how** the control is met." } } },
              "ps-1_stmt.b.2" : 
              { "uuid" : "6926c688-3fb2-4ab8-9acb-cff0b5acd365",
                "description" : "Ignore.",
                "by-components" : 
                { "60f92bcf-f353-4236-9803-2a5d417555f4" : 
                  { "uuid" : "2f9c701a-0f3e-4e3d-beae-debb08c406ed",
                    "description" : "For the portion of the control satisfied by the service provider, describe\n                        **how** the control is met." } } } } },
          
          { "uuid" : "789e6c0f-acda-4a94-9b48-7d41dd4c607c",
            "control-id" : "ra-1",
            "properties" : 
            [ 
              { "name" : "planned-completion-date",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "2020-11-27Z" } ],
            "annotations" : 
            [ 
              { "name" : "implementation-status",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "planned",
                "remarks" : "Describe the plan to complete the implementation." },
              
              { "name" : "control-origination",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "sp-system" } ],
            "responsible-roles" : 
            { "program-director" : 
              {  } },
            "parameter-settings" : 
            { "ra-1_prm_1" : 
              { "value" : "[replace with list of personnel or roles]" },
              "ra-1_prm_2" : 
              { "value" : "[specify frequency]" },
              "ra-1_prm_3" : 
              { "value" : "[specify frequency]" } },
            "statements" : 
            { "ra-1_stmt.a" : 
              { "uuid" : "8fe541ea-0920-42d0-8561-4e08f04d796c",
                "description" : "Ignore.",
                "by-components" : 
                { "60f92bcf-f353-4236-9803-2a5d417555f4" : 
                  { "uuid" : "5894d92b-05bf-4fc4-85dc-f5c37e112bc4",
                    "description" : "For the portion of the control satisfied by the service provider, describe\n                        **how** the control is met." } } },
              "ra-1_stmt.b.1" : 
              { "uuid" : "b0e9ed47-fe83-485d-8d79-979833543a83",
                "description" : "Ignore.",
                "by-components" : 
                { "60f92bcf-f353-4236-9803-2a5d417555f4" : 
                  { "uuid" : "c90ad6ee-5a40-4996-8e6c-d85ff3f7559e",
                    "description" : "For the portion of the control satisfied by the service provider, describe\n                        **how** the control is met." } } },
              "ra-1_stmt.b.2" : 
              { "uuid" : "d9a38f95-ded1-4d1d-afe2-242987222ebd",
                "description" : "Ignore.",
                "by-components" : 
                { "60f92bcf-f353-4236-9803-2a5d417555f4" : 
                  { "uuid" : "d6f6ac98-4f15-45f2-9ecc-4447e96af44f",
                    "description" : "For the portion of the control satisfied by the service provider, describe\n                        **how** the control is met." } } } } },
          
          { "uuid" : "55358f60-db9b-4d75-a313-5fa6c328273c",
            "control-id" : "sa-1",
            "properties" : 
            [ 
              { "name" : "planned-completion-date",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "2020-11-27Z" } ],
            "annotations" : 
            [ 
              { "name" : "implementation-status",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "planned",
                "remarks" : "Describe the plan to complete the implementation." },
              
              { "name" : "control-origination",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "sp-system" } ],
            "responsible-roles" : 
            { "program-director" : 
              {  } },
            "parameter-settings" : 
            { "sa-1_prm_1" : 
              { "value" : "[replace with list of personnel or roles]" },
              "sa-1_prm_2" : 
              { "value" : "[specify frequency]" },
              "sa-1_prm_3" : 
              { "value" : "[specify frequency]" } },
            "statements" : 
            { "sa-1_stmt.a" : 
              { "uuid" : "ae3f64be-2e62-4347-b06a-727bc28e4f9b",
                "description" : "Ignore.",
                "by-components" : 
                { "60f92bcf-f353-4236-9803-2a5d417555f4" : 
                  { "uuid" : "e5864f16-83f2-4faf-b7be-0810c6e58fc4",
                    "description" : "For the portion of the control satisfied by the service provider, describe\n                        **how** the control is met." } } },
              "sa-1_stmt.b.1" : 
              { "uuid" : "959519a9-3e12-47bc-8d76-50d9ab0b6544",
                "description" : "Ignore.",
                "by-components" : 
                { "60f92bcf-f353-4236-9803-2a5d417555f4" : 
                  { "uuid" : "bed8f51a-1773-493c-8167-c83712e03f01",
                    "description" : "For the portion of the control satisfied by the service provider, describe\n                        **how** the control is met." } } },
              "sa-1_stmt.b.2" : 
              { "uuid" : "9daa3848-9672-469c-9aa0-f363e3339123",
                "description" : "Ignore.",
                "by-components" : 
                { "60f92bcf-f353-4236-9803-2a5d417555f4" : 
                  { "uuid" : "518d4987-9436-4c1f-9e07-afa6b332f124",
                    "description" : "For the portion of the control satisfied by the service provider, describe\n                        **how** the control is met." } } } } },
          
          { "uuid" : "9e2852c6-f48a-47b2-9ea5-77cbbb42b365",
            "control-id" : "sc-1",
            "properties" : 
            [ 
              { "name" : "planned-completion-date",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "2020-11-27Z" } ],
            "annotations" : 
            [ 
              { "name" : "implementation-status",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "planned",
                "remarks" : "Describe the plan to complete the implementation." },
              
              { "name" : "control-origination",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "sp-system" } ],
            "responsible-roles" : 
            { "program-director" : 
              {  } },
            "parameter-settings" : 
            { "sc-1_prm_1" : 
              { "value" : "[replace with list of personnel or roles]" },
              "sc-1_prm_2" : 
              { "value" : "[specify frequency]" },
              "sc-1_prm_3" : 
              { "value" : "[specify frequency]" } },
            "statements" : 
            { "sc-1_stmt.a" : 
              { "uuid" : "5e2e8372-c13b-4cf5-90c5-e8833a9fe241",
                "description" : "Ignore.",
                "by-components" : 
                { "60f92bcf-f353-4236-9803-2a5d417555f4" : 
                  { "uuid" : "88cfadba-043b-483b-8032-73344aa53c96",
                    "description" : "For the portion of the control satisfied by the service provider, describe\n                        **how** the control is met." } } },
              "sc-1_stmt.b.1" : 
              { "uuid" : "8166980a-86c0-497d-87e4-453adfd0d4bd",
                "description" : "Ignore.",
                "by-components" : 
                { "60f92bcf-f353-4236-9803-2a5d417555f4" : 
                  { "uuid" : "9abaeb64-56d2-48a1-bd8d-7b55411d31ca",
                    "description" : "For the portion of the control satisfied by the service provider, describe\n                        **how** the control is met." } } },
              "sc-1_stmt.b.2" : 
              { "uuid" : "eeea34ff-18ab-4c35-bf32-c74dbf746e7b",
                "description" : "Ignore.",
                "by-components" : 
                { "60f92bcf-f353-4236-9803-2a5d417555f4" : 
                  { "uuid" : "ad20ff50-8a7c-4ffc-a918-260960f6fb42",
                    "description" : "For the portion of the control satisfied by the service provider, describe\n                        **how** the control is met." } } } } },
          
          { "uuid" : "81ba4fe8-1649-437b-9ecf-367fd87336e6",
            "control-id" : "si-1",
            "properties" : 
            [ 
              { "name" : "planned-completion-date",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "2020-11-27Z" } ],
            "annotations" : 
            [ 
              { "name" : "implementation-status",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "planned",
                "remarks" : "Describe the plan to complete the implementation." },
              
              { "name" : "control-origination",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "sp-system" } ],
            "responsible-roles" : 
            { "program-director" : 
              {  } },
            "parameter-settings" : 
            { "si-1_prm_1" : 
              { "value" : "[replace with list of personnel or roles]" },
              "si-1_prm_2" : 
              { "value" : "[specify frequency]" },
              "si-1_prm_3" : 
              { "value" : "[specify frequency]" } },
            "statements" : 
            { "si-1_stmt.a" : 
              { "uuid" : "915b10d2-2275-4d86-951a-eec23f9ee77a",
                "description" : "Ignore.",
                "by-components" : 
                { "60f92bcf-f353-4236-9803-2a5d417555f4" : 
                  { "uuid" : "682311e7-e3f7-4d94-acf9-131149887fda",
                    "description" : "For the portion of the control satisfied by the service provider, describe\n                        **how** the control is met." } } },
              "si-1_stmt.b.1" : 
              { "uuid" : "2a5a6f7f-aeea-4ea4-be1e-859df4bf7521",
                "description" : "Ignore.",
                "by-components" : 
                { "60f92bcf-f353-4236-9803-2a5d417555f4" : 
                  { "uuid" : "80ee0fe9-7f87-4dfa-887a-ac3bb2131943",
                    "description" : "For the portion of the control satisfied by the service provider, describe\n                        **how** the control is met." } } },
              "si-1_stmt.b.2" : 
              { "uuid" : "c152bbde-57fc-4864-ac51-861bd8bb83b4",
                "description" : "Ignore.",
                "by-components" : 
                { "60f92bcf-f353-4236-9803-2a5d417555f4" : 
                  { "uuid" : "78e8f2bb-67d7-49d3-a993-ce4bedcfbc47",
                    "description" : "For the portion of the control satisfied by the service provider, describe\n                        **how** the control is met." } } } } } ] },
      "back-matter" : 
      { "resources" : 
        [ 
          { "uuid" : "3a5ca2de-0f66-47e6-844d-6ccdf214b767",
            "title" : "FedRAMP Applicable Laws and Regulations",
            "properties" : 
            [ 
              { "name" : "conformity",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "fedramp-citations" } ],
            "rlinks" : 
            [ 
              { "href" : "https:\/\/www.fedramp.gov\/assets\/resources\/templates\/SSP-A12-FedRAMP-Laws-and-Regulations-Template.xlsx" } ] },
          
          { "uuid" : "12da89ef-51dd-4404-948d-e9f0e25b961e",
            "title" : "FedRAMP Master Acronym and Glossary",
            "properties" : 
            [ 
              { "name" : "conformity",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "fedramp-acronyms" } ],
            "rlinks" : 
            [ 
              { "href" : "https:\/\/www.fedramp.gov\/assets\/resources\/documents\/FedRAMP_Master_Acronym_and_Glossary.pdf" } ] },
          
          { "uuid" : "d45612a9-cf25-4ef6-b2dd-69e38ba2967a",
            "title" : "[SAMPLE]Name or Title of Document",
            "properties" : 
            [ 
              { "name" : "type",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "law" },
              
              { "name" : "publication",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "Publication Date" } ],
            "document-ids" : 
            [ 
              { "type" : "doi",
                "identifier" : "Identification Number" } ],
            "rlinks" : 
            [ 
              { "href" : "https:\/\/domain.example\/path\/to\/document.pdf" } ] },
          
          { "uuid" : "a8a0cc81-800f-479f-93d3-8b8743d9b98d",
            "title" : "[SAMPLE]Privacy-Related Law Citation",
            "properties" : 
            [ 
              { "name" : "type",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "law" },
              
              { "name" : "type",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "pii" },
              
              { "name" : "publication",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "Publication Date" } ],
            "document-ids" : 
            [ 
              { "type" : "doi",
                "identifier" : "Identification Number" } ],
            "rlinks" : 
            [ 
              { "href" : "https:\/\/domain.example\/path\/to\/document.pdf" } ] },
          
          { "uuid" : "545e75c3-537f-48fe-9630-95337916d982",
            "title" : "[SAMPLE]Regulation Citation",
            "properties" : 
            [ 
              { "name" : "type",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "regulation" },
              
              { "name" : "publication",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "Publication Date" } ],
            "document-ids" : 
            [ 
              { "type" : "doi",
                "identifier" : "Identification Number" } ],
            "rlinks" : 
            [ 
              { "href" : "https:\/\/domain.example\/path\/to\/document.pdf" } ] },
          
          { "uuid" : "9d6cf2b4-8e88-4040-a33c-7bc206553a1a",
            "title" : "[SAMPLE]Interconnection Security Agreement Title",
            "properties" : 
            [ 
              { "name" : "publication",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "Document Date" },
              
              { "name" : "version",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "Document Version" } ] },
          
          { "uuid" : "31a46c4f-2959-4287-bc1c-67297d7da60b",
            "desc" : "CSP Logo",
            "properties" : 
            [ 
              { "name" : "conformity",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "prepared-for-logo" },
              
              { "name" : "conformity",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "csp-logo" } ],
            "rlinks" : 
            [ 
              { "href" : ".\/logo.png",
                "media-type" : "image\/png" } ],
            "attachments" : 
            [ 
              { "value" : "00000000" } ] },
          
          { "uuid" : "c5866ad8-8ed7-49b4-844a-0276fa9f8f51",
            "desc" : "Preparer Logo",
            "properties" : 
            [ 
              { "name" : "conformity",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "prepared-by-logo" } ],
            "rlinks" : 
            [ 
              { "href" : ".\/party-1-logo.png",
                "media-type" : "image\/png" } ],
            "attachments" : 
            [ 
              { "value" : "00000000" } ] },
          
          { "uuid" : "0846b6ef-cfa4-4bb3-8280-717f7e7b04d4  ",
            "desc" : "FedRAMP Logo",
            "properties" : 
            [ 
              { "name" : "conformity",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "fedramp-logo" } ],
            "rlinks" : 
            [ 
              { "href" : "https:\/\/github.com\/GSA\/fedramp-automation\/raw\/master\/assets\/FedRAMP_LOGO.png" } ] },
          
          { "uuid" : "2c1747d6-874a-49a2-8488-2fd9735416bf",
            "desc" : "3PAO Logo",
            "properties" : 
            [ 
              { "name" : "conformity",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "3pao-logo" } ],
            "rlinks" : 
            [ 
              { "href" : ".\/logo.png",
                "media-type" : "image\/png" } ],
            "attachments" : 
            [ 
              { "value" : "00000000" } ] },
          
          { "uuid" : "d2eb3c18-6754-4e3a-a933-03d289e3fad5",
            "desc" : "The primary authorization boundary diagram.",
            "rlinks" : 
            [ 
              { "href" : ".\/diagrams\/boundary.png" } ],
            "attachments" : 
            [ 
              { "value" : "00000000" } ],
            "remarks" : "Section 9.2, Figure 9-1 Authorization Boundary Diagram (graphic)\\n\\nThis should be referenced in the\n               system-characteristics\/authorization-boundary\/diagram\/link\/@href flag using a value\n               of \\\"#d2eb3c18-6754-4e3a-a933-03d289e3fad5\\\"" },
          
          { "uuid" : "61081e81-850b-43c1-bf43-1ecbddcb9e7f",
            "desc" : "The primary network diagram.",
            "rlinks" : 
            [ 
              { "href" : ".\/diagrams\/network.png" } ],
            "attachments" : 
            [ 
              { "value" : "00000000" } ],
            "remarks" : "Section 9.4, Figure 9-2 Network Diagram (graphic)\\n\\nThis should be referenced in the\n               system-characteristics\/network-architecture\/diagram\/link\/@href flag using a value\n               of \\\"#61081e81-850b-43c1-bf43-1ecbddcb9e7f\\\"" },
          
          { "uuid" : "ac5d7535-f3b8-45d3-bf3b-735c82c64547",
            "desc" : "The primary data flow diagram.",
            "rlinks" : 
            [ 
              { "href" : ".\/diagrams\/dataflow.png" } ],
            "attachments" : 
            [ 
              { "value" : "00000000" } ],
            "remarks" : "Section 10, Figure 10-1 Data Flow Diagram (graphic)\\n\\nThis should be referenced in the\n               system-characteristics\/data-flow\/diagram\/link\/@href flag using a value\n               of \\\"#ac5d7535-f3b8-45d3-bf3b-735c82c64547\\\"" },
          
          { "uuid" : "090ab379-2089-4830-b9fd-26d0729e22e9",
            "title" : "Policy Title",
            "desc" : "Policy document",
            "properties" : 
            [ 
              { "name" : "type",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "policy" },
              
              { "name" : "publication",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "Document Date" },
              
              { "name" : "version",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "Document Version" } ],
            "rlinks" : 
            [ 
              { "href" : ".\/sample_policy.pdf" } ],
            "attachments" : 
            [ 
              { "value" : "00000000" } ],
            "remarks" : "Table 15-1 Attachments: Policy Attachment" },
          
          { "uuid" : "ab300133-d749-4abb-b858-1cd6ffd8af9e",
            "title" : "Policy Title",
            "desc" : "Policy document",
            "properties" : 
            [ 
              { "name" : "type",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "policy" },
              
              { "name" : "publication",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "Document Date" },
              
              { "name" : "version",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "Document Version" } ],
            "rlinks" : 
            [ 
              { "href" : ".\/sample_policy.pdf" } ],
            "attachments" : 
            [ 
              { "value" : "00000000" } ],
            "remarks" : "Table 15-1 Attachments: Policy Attachment" },
          
          { "uuid" : "1002a58e-9e11-4aa6-9ab4-2bde52995952",
            "title" : "Procedure Title",
            "desc" : "Procedure document",
            "properties" : 
            [ 
              { "name" : "type",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "procedure" },
              
              { "name" : "publication",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "Document Date" },
              
              { "name" : "version",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "Document Version" } ],
            "rlinks" : 
            [ 
              { "href" : ".\/sample_procedure.pdf" } ],
            "attachments" : 
            [ 
              { "value" : "00000000" } ],
            "remarks" : "Table 15-1 Attachments: Procedure Attachment" },
          
          { "uuid" : "4bb1e2e5-261c-4b5c-b22c-e1627c2e8be6",
            "title" : "Procedure Title",
            "desc" : "Procedure document",
            "properties" : 
            [ 
              { "name" : "type",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "procedure" },
              
              { "name" : "publication",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "Document Date" },
              
              { "name" : "version",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "Document Version" } ],
            "rlinks" : 
            [ 
              { "href" : ".\/sample_procedure.pdf" } ],
            "attachments" : 
            [ 
              { "value" : "00000000" } ],
            "remarks" : "Table 15-1 Attachments: Procedure Attachment" },
          
          { "uuid" : "90a128ac-c850-48f6-8fff-a55692f80b41",
            "title" : "User's Guide",
            "desc" : "User's Guide",
            "properties" : 
            [ 
              { "name" : "conformity",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "user-guide" },
              
              { "name" : "type",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "guide" },
              
              { "name" : "publication",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "Document Date" },
              
              { "name" : "version",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "Document Version" } ],
            "rlinks" : 
            [ 
              { "href" : ".\/sample_guide.pdf" } ],
            "attachments" : 
            [ 
              { "value" : "00000000" } ],
            "remarks" : "Table 15-1 Attachments: User's Guide Attachment" },
          
          { "uuid" : "fab59751-b855-40cb-93c1-492562e20e18",
            "title" : "Privacy Impact Assessment",
            "properties" : 
            [ 
              { "name" : "conformity",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "privacy-impact-assessment" },
              
              { "name" : "publication",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "Document Date" },
              
              { "name" : "version",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "Document Version" } ],
            "rlinks" : 
            [ 
              { "href" : ".\/pia.docx" } ],
            "attachments" : 
            [ 
              { "filename" : "pia.docx",
                "value" : "00000000" } ],
            "remarks" : "Table 15-1 Attachments: Privacy Impact Assessment" },
          
          { "uuid" : "489112e1-57f2-4c29-8dd0-95b1442fbf3b",
            "title" : "Document Title",
            "desc" : "Rules of Behavior",
            "properties" : 
            [ 
              { "name" : "conformity",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "rules-of-behavior" },
              
              { "name" : "type",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "rob" },
              
              { "name" : "publication",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "Document Date" },
              
              { "name" : "version",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "Document Version" } ],
            "rlinks" : 
            [ 
              { "href" : "https:\/\/sample" } ],
            "attachments" : 
            [ 
              { "value" : "00000000" } ],
            "remarks" : "Table 15-1 Attachments: Rules of Behavior (ROB)" },
          
          { "uuid" : "c7860916-f2f4-43aa-b578-d48cf8e6d381",
            "title" : "Document Title",
            "desc" : "Contingency Plan (CP)",
            "properties" : 
            [ 
              { "name" : "type",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "plan" },
              
              { "name" : "publication",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "Document Date" },
              
              { "name" : "version",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "Document Version" } ],
            "rlinks" : 
            [ 
              { "href" : "https:\/\/sample" } ],
            "attachments" : 
            [ 
              { "value" : "00000000" } ],
            "remarks" : "Table 15-1 Attachments: Contingency Plan (CP) Attachment" },
          
          { "uuid" : "ab56cf27-0dae-40d6-89b7-d750137309af",
            "title" : "Document Title",
            "desc" : "Configuration Management (CM) Plan",
            "properties" : 
            [ 
              { "name" : "type",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "plan" },
              
              { "name" : "publication",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "Document Date" },
              
              { "name" : "version",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "Document Version" } ],
            "rlinks" : 
            [ 
              { "href" : "https:\/\/sample" } ],
            "attachments" : 
            [ 
              { "value" : "00000000" } ],
            "remarks" : "Table 15-1 Attachments: Configuration Management (CM) Plan Attachment" },
          
          { "uuid" : "3f771ab5-8016-4571-98d1-f0fb962e15e2",
            "title" : "Document Title",
            "desc" : "Incident Response (IR) Plan",
            "properties" : 
            [ 
              { "name" : "type",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "plan" },
              
              { "name" : "publication",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "Document Date" },
              
              { "name" : "version",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "Document Version" } ],
            "rlinks" : 
            [ 
              { "href" : "https:\/\/sample" } ],
            "attachments" : 
            [ 
              { "value" : "00000000" } ],
            "remarks" : "Table 15-1 Attachments: Incident Response (IR) Plan Attachment" },
          
          { "uuid" : "49fb4631-1da2-41ca-b0b3-e1b1006d4025",
            "title" : "Separation of Duties Matrix",
            "desc" : "Separation of Duties Matrix",
            "properties" : 
            [ 
              { "name" : "publication",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "Document Date" },
              
              { "name" : "version",
                "ns" : "https:\/\/fedramp.gov\/ns\/oscal",
                "value" : "Document Version" } ],
            "rlinks" : 
            [ 
              { "href" : "https:\/\/sample" } ],
            "attachments" : 
            [ 
              { "value" : "00000000" } ],
            "remarks" : "Table 15-1 Attachments: Separation of Duties Matrix Attachment" },
          
          { "uuid" : "9f1aae37-7359-411f-86c1-768aaab85e63",
            "title" : "FedRAMP High Baseline",
            "rlinks" : 
            [ 
              { "href" : "https:\/\/raw.githubusercontent.com\/usnistgov\/OSCAL\/v1.0.0-milestone3\/content\/fedramp.gov\/xml\/FedRAMP_HIGH-baseline_profile.xml",
                "media-type" : "application\/xml" } ],
            "remarks" : "Pointer to High baseline content in OSCAL." },
          
          { "uuid" : "890170c3-d4fa-4d25-ab96-8e4bf7cc237c",
            "title" : "FedRAMP Moderate Baseline",
            "rlinks" : 
            [ 
              { "href" : "https:\/\/raw.githubusercontent.com\/usnistgov\/OSCAL\/v1.0.0-milestone3\/content\/fedramp.gov\/xml\/FedRAMP_MODERATE-baseline_profile.xml",
                "media-type" : "application\/xml" } ],
            "remarks" : "Pointer to Moderate baseline content in OSCAL." },
          
          { "uuid" : "2acaf846-5496-4d36-8565-9a15b48aef2c",
            "title" : "FedRAMP Low Baseline",
            "rlinks" : 
            [ 
              { "href" : "https:\/\/raw.githubusercontent.com\/usnistgov\/OSCAL\/v1.0.0-milestone3\/content\/fedramp.gov\/xml\/FedRAMP_LOW-baseline_profile.xml",
                "media-type" : "application\/xml" } ],
            "remarks" : "Pointer to Low baseline content in OSCAL." } ] } } }