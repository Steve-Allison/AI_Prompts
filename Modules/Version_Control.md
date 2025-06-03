# Module Version Control

This document tracks the version compatibility between different modules to ensure smooth integration and functionality.

## Current Versions

| Module                               | Current Version | Release Date | Dependencies                                                                   |
| ------------------------------------ | --------------- | ------------ | ------------------------------------------------------------------------------ |
| `Cognitive_Keyword_Watchlist_Module` | 1.0.0           | 2025-05-10   | None                                                                           |
| `Pedagogy_Module`                    | 1.0.0           | 2025-05-10   | None                                                                           |
| `Learning_Activity_Generator_Module` | 1.0.0           | 2025-05-12   | `Cognitive_Keyword_Watchlist_Module` v1.0+                                     |
| `Misconception_Check_Module`         | 1.1.0           | 2025-06-03   | `Cognitive_Keyword_Watchlist_Module` v1.0+                                     |
| `Differentiation_Scaffolding_Module` | 1.1.0           | 2025-06-03   | `Learning_Activity_Generator_Module` v1.0+, `Misconception_Check_Module` v1.0+ |
| `Visual_Style_Module`                | 1.0.0           | 2025-05-15   | None                                                                           |
| `Accessibility_Module`               | 1.0.0           | 2025-05-15   | `Visual_Style_Module` v1.0+                                                    |
| `Instructional_Segment_Mapper`       | 1.0.0           | 2025-05-18   | `Cognitive_Keyword_Watchlist_Module` v1.0+, `Pedagogy_Module` v1.0+            |

## Versioning Scheme

We follow [Semantic Versioning](https://semver.org/):

- **MAJOR** version for incompatible API changes
- **MINOR** version for added functionality in a backward-compatible manner
- **PATCH** version for backward-compatible bug fixes

## Update Log

### 2025-06-03 - Version 1.1.0 Updates

- Enhanced `Differentiation_Scaffolding_Module` with better cross-module integration
- Updated `Misconception_Check_Module` to align with new scaffolding approaches
- Added comprehensive version control documentation

### 2025-05-18 - Version 1.0.0 Initial Release

- Initial release of all core modules
- Established baseline versioning and dependencies

## Compatibility Matrix

| Module                                      | Compatible With                                                                    | Incompatible With       |
| ------------------------------------------- | ---------------------------------------------------------------------------------- | ----------------------- |
| `Differentiation_Scaffolding_Module` v1.1.0 | `Learning_Activity_Generator_Module` v1.0+<br>`Misconception_Check_Module` v1.1.0+ | Any version below 1.0.0 |
| `Misconception_Check_Module` v1.1.0         | `Cognitive_Keyword_Watchlist_Module` v1.0+                                         | None                    |
| `Learning_Activity_Generator_Module` v1.0.0 | `Cognitive_Keyword_Watchlist_Module` v1.0+                                         | None                    |

## Update Instructions

1. **Check Dependencies**: Before updating any module, verify that all dependent modules are at compatible versions.
2. **Backup**: Always back up your current implementation before updating.
3. **Test**: After updating, test all integrated functionality.
4. **Document**: Update your project's version control documentation.

## Troubleshooting

If you encounter issues after an update:

1. Check the version compatibility matrix above
2. Verify all dependencies are at required versions
3. Consult the specific module's changelog for breaking changes
4. If issues persist, roll back to the previous working version and report the issue

## Future Roadmap

### Planned Updates (Q3 2025)

- Version 1.2.0 of `Differentiation_Scaffolding_Module` with enhanced AI-powered scaffolding
- New module for learning analytics integration
- Enhanced cross-module validation tools

### Under Consideration

- Automated version compatibility checking
- Module dependency visualization tool
- Self-updating documentation based on module versions
