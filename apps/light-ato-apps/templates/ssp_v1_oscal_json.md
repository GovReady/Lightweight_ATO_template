id: ssp_v1_oscal_json
format: json
title: SSP v1 (OSCAL/JSON)
...
{
  "system-security-plan": {
    "uuid": "2fa78e07-74ef-4cd6-8124-bc0050c0c4df",
    "metadata": {
      "title": "{{ project.system_info.system_name }}",
      "last-modified": "{{ oscal.last_modified }}",
      "version": "{{ oscal.version }}",
      "oscal-version": "1.0.0rc1"
    },
    "import-profile": {
      "href": "{{ oscal.profile }}"
    },
    "system-characteristics": {
      "system-ids": [
        {
          "id": "{{ oscal.system_id }}"
        }
      ],
      "system-name": "{{ project.system_info.system_name }}",
      "system-name-short": "{{ project.system_info.system_short_name }}",
      "description": "{{ project.system_info.system_description }}",
      "security-sensitivity-level": "{{ project.fisma_level.fisma_level }}",
      "system-information": {
        "information-types": [
          {
            "title": "{{ oscal.system_information_type_title }}",
            "description": "{{ oscal.system_information_type_description }}",
            "confidentiality-impact": {
              "base": "{{ oscal.system_information_type_confidentiality_impact }}"
            },
            "integrity-impact": {
              "base": "{{ oscal.system_information_type_integrity_impact }}"
            },
            "availability-impact": {
              "base": "{{ oscal.system_information_type_availability_impact }}"
            }
          }
        ]
      },
      "security-impact-level": {
        "security-objective-confidentiality": "{{ oscal.system_security_impact_level_confidentiality }}",
        "security-objective-integrity": "{{ oscal.system_security_impact_level_integrity }}",
        "security-objective-availability": "{{ oscal.system_security_impact_level_availability }}"
      },
      "status": {
        "state": "{{ project.system_info_technical.system_status.text }}"
      },
      "authorization-boundary": {
        "description": "{{ oscal.system_authorization_boundary }}"
      }
    },

    "system-implementation": {
      "users": {
        "%dict": "user in project.system_info_technical.security_impact_users",
        "%item": {
           "%key": "{{ oscal.make_uuid() }}",
           "title": "{{ user.answer['Role'] }}"
        }
      },
      "components": {
        "%dict": "component in oscal.components",
        "%item": {
           "%key": "{{ component.uuid }}",
           "title": "{{ component.title }}",
           "description": "{{ component.description | safe }}",
           "status": {
             "state": "{{ project.system_info_technical.system_status.text }}"
           }
        }
      },
      "control-implementation": {
        "description": "Control implementations",
        "implemented-requirements": {
          "%for": "requirement in oscal.implemented_requirements",
           "%loop": {
               "uuid": "{{ requirement.uuid }}",
               "control_id": "{{ requirement.control_id }}",
               "parameter-settings": {
                 "%for": "setting in requirement.parameter_settings",
                 "%loop": {
                    "param_id": "{{ setting.param_id }}",
                    "values": ["{{ setting.value }}"]
                  }
               },
               "statements": {
                 "%dict": "statement in requirement.statements",
                 "%item": {
                   "%key": "{{ statement.id }}",
                   "uuid": "{{ statement.uuid }}",
                   "by-components": {
                     "%dict": "by_component in statement.by_components",
                     "%item": {
                        "%key": "{{ by_component.component_uuid }}",
                        "description": "{{ by_component.description | safe }}"
                     }
                   }
                 }
               }
           }
        }
      }
    }
  }
}
