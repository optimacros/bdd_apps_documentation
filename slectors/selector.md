# Селекторы

| Name Selector  | Class                                          | Tag or any attribute  |  Exists attr |
| -------------  | -------------                                  | -------------         |  -------------         |
| global Loader  | GlobalLoader__Overlay                          |                       |                        |
| loader         | LocalLoader__Container                         |                       |                        |
| any Loader     | GlobalLoader__Overlay , LocalLoader__Container |                       |                        |
| search Results | SearchResultList                               |                       | yes                    |
| modal                | ReactModal__Content                      |                       |                        |
| output Macros Dialog | OutputMacrosDialog-module__Content       |                       |                        |
| modal Color Picker   | Color__picker                            |                       |                        |
| modal Title          | Modal__Header_Title                      |                       | yes                    |
| grid Title           | GridTitle-module__Title                  |                       | yes                    |
| modal Form Content   | ModalFormDialog__InsertModuleDialog      |                       |                        |
| toolbar Of Toolbar Settings | ToolbarSettingsDialogMenu-module  |                       |                        |
| button             |                                            |  button               | yes                    |
| enabled Button     | not class ***Disabled***                   |  button               | yes                    |
| configurator Dnd Element |                                      |  button               | yes                    |
| configurator Dnd Element Button | ProgressBarContainer          |  name                 | yes                    |
| menu Item                | mdl-portalmenu__item  , menuItem , react-contextmenu-item |  | yes                    |
|                          | rc-dropdown-menu-item  , rc-dropdown-menu-submenu         |  |                        |
| grid Context Menu        | gridContextMenu , react-contextmenu  |                       |                        |
| notification             | snackbar                             |                       | yes                    |
| recalculate Notifications | HeaderNotifier__notificationContainer_Title  |              | yes                    |
| recalculate Notifications Title | HeaderNotifier__notificationContainer_Title  |        |                        |
| popup Menu                | mdl-portalmenu__list , rc-dropdown-menu-root  |             |                        |
| grid Comments Editor      | GridCommentsElement__Message        |                       |                        |
| grid Error Dialog         | ErrorDialog__messageContainer       |                       |                        |
| tab Header                | TabHeader__TabButton__              |                       | yes                    |
| tabs Container            | TabsContainer                       |                       |                        |
| main Tabs Header Container| MainTabs__HeaderContainer           |                       |                        |
| Tabs Header Container     | TabHeader__TabHeaderContainer       |                       |                        |
| toolbar                   |                                     | navigation            |                        |
| dashboard Toolbar         | dashboardTabHeader                  |                       |                        |
| toolbar Right Side        | RightToolbarButtons                 |                       |                        |
| validation Error          | error                               |                       |                        |
| tree Menu                 | BaseMenu__Menu , FilterMenu__Container |                    |                        |
| tree Menu Element         | BaseMenu__Element                   |                       | yes                    |
| filter Element            | BaseMenu__Element                   |                       | yes                    |
| tree Menu Title           | TreeMenu__title                     |                       | yes                    |
| tree Menu Arrow           | BaseMenu__ButtonArrow               |                       |                        |
| custom Button Container   | CustomButton-module__Container      |                       | yes                    |
| button Settings           | CustomButton-module__IconContainer  |                       |                        |
| sample Value              | Number__SampleValue , Text-module__SampleValue |            | yes                    |
| tree Element Container    | BaseMenu__ListElement               | name , data-name      | yes                    |

[Инструкция поиска селекторов](../slectors/instructionSelector.md)

[Инструкция по добавлению нового селектора]()

[Оглавление](../README.md)