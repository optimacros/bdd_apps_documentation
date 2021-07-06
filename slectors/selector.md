# Селекторы

| Name Selector  | Class                                          | Tag or any contains   |  Exists attr |
| -------------  | -------------                                  | -------------         |  -------------         |
| global Loader  | GlobalLoader__Overlay                          |                       |                        |
| loader         | LocalLoader__Container                         |                       |                        |
| any Loader     | GlobalLoader__Overlay , LocalLoader__Container |                       |                        |
| search Results | SearchResultList                               |                       | yes                    |
| search Input   | Search__inputElement , FilterInput__Field , SearchButton__Input |      | yes                    |
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
| Drive Landing             | Content__Wrapper                    |                       |                        |
| drive Landing Page        | DriveLanding__Container             |                       |                        |
| header View               | Header__View                        |                       |                        |
| model Item                | ModelsItemRow-module__Container ,   |                       | yes                    |
|                           | ModelsItemCard-module__Container    |                       |                        |
| status Offline            | module__Status_offline              |                       | yes                    |
| folder Item               | FoldersItemRow-module__Container    |                       | yes                    |
|                           | FoldersItemCard-module__Container   |                       |                        |
| model Row                 | ModelsItemRow-module__Container     |                       | yes                    |
| folder Row                | FoldersItemRow-module__Container    |                       | yes                    |
| model Card                | ModelsItemCard-module__Container    |                       | yes                    |
| folder Card               | FoldersItemCard-module__Container   |                       | yes                    |
| left Panel Element        | ModelLink__Container                |                       | yes                    |
| memory Indicator Container| MemoryIndicator-module__Container   |                       | yes                    |
| folder Count              | FoldersItemCard-module__CountModels |                       | yes                    |
| user Menu                 | UserMenu__userMenu                  |                       | yes                    |
| upper Left Cell           | TopLeftCell                         |                       |                        |
| import Manager List       | ImportManager_ListColumn            |                       |                        |
| modal Import Zone         | ImportManager__DnDZone              |                       |                        |
| import Manager Item       | ImportManager_ListColumn            |                       | yes                    |
| calendar Day Number       |                                     | day                   | yes                    |
| selection Body Layout     | GridSelectionBodyLayout             |                       |                        |
| selection Cols Layout     | GridSelectionColsLayout             |                       |                        |
| selection Rows Layout     | GridSelectionRowsLayout             |                       |                        |
| selection Left Top Layout | GridSelectionLeftTopLayout          |                       |                        |
| count Clusters            | Input__inputElement                 |                       |                        |
| thumb Inner               | RangeSlider-module__ThumbInner      |                       | yes                    |
| modal Search Input        | CreateModuleDialogBasicTab-module__SearchInput |            |                        |
| optimizer Input           | OptimizerTab-module__FormulaLine    |                       | yes                    |
| clear Result Search       | FilterInput__ClearButtonIcon        |                       |                        |
| scroller                  | scrollContainer , ScrollContainer , scrollContainer , ScrollContainer |   |          |
|                           | SelectBox__values , rc-dropdown-menu-vertical , ListElements-module__Content |   |   |
| basic Tab Card Setting    | BasicTabCardSetting                 |                       |                        |
| advanced Tab Card Setting | AdvancedTabCardSetting              |                       |                        |
| footer Copyright          | MainTabs__FooterCopyright           |                       |                        |
| grid Counter              | GridCounter                         |                       |                        |
| grid Counter Date         | GridCounterLastSyncDate             |                       |                        |
| grid Counter Count        | GridCounterCount                    |                       | yes                    |
| grid Counter Average      | GridCounterAverage                  |                       | yes                    |
| grid Counter Summ         | GridCounterSumm                     |                       | yes                    |
| grid Counter Filled Cells Count | GridCounterFilledCellsCount   |                       | yes                    |
| tag Title Container       | TagsItem__Container                 |                       |                        |
| grid Comments Container   | GridComments__Container             |                       |                        |
| header Comments           | Contents-module__headerCommentsClose|                       |                        |
| text Area Card Editor     | ql-container ql-snow                |                       |                        |
| card Of Context Table     | recharts-responsive-container , MapWithObjects-module__Container | |                 |
|                           | ImagesWithObjects-module__Container |                       |                        |
| dashboard Card            | BaseCard__content , Cards__Card     |                       |                        |
| toolbar Textarea Card     | BaseCard__content , Cards__Card     |                       |                        |
| textarea Card Button      |                                     |                       | yes                    |
| markdown Card             | BaseCard__content , Markdown        |                       |                        |
| dashboard Card With Id Name |                                   | name , data-name      | yes                    |
| markdown Editor           | MarkdownEditor__MarkdownEditorTextarea |                    |                        |
| markdown Preview          | MarkdownEditor__MarkdownEditorHtml  |                       |                        |
| media File                | MediaFileItem__preview              |                       |                        |
| modal Media Files         | MediaFileItem__preview              |                       |                        |
| comment By User           | GridCommentsElement__Container , GridCommentsElement__Info |  | yes                  |
| zoom Slider               | ZoomSlider                          |                       |                        |
| main Tabs                 | MainTabs__Container                 |                       |                        |
| chart Scroll Conteiner    | ChartsDialog__config                |                       |                        |
| chart Tooltip             | recharts-tooltip-item , HoverInfo__HoverInfo , |            | yes                    |
|                           | FunnelChart__tooltip , ChartTooltip-module__Container |     |                        |
| zone Size Card            | react-resizable-handle              |                       |                        |
| grid Container            | Grid__GridScrollNode                |                       |                        |
| list Elements             | ListElements-module__Container      |                       |                        |
| list Element              | ListElements-module__Element        |                       | yes                    |
| progress Bar              | ProgressBar__Button                 |                       |                        |
| field                     | Fields__InputContainer              |                       | yes                    |
| target Formula Line       | TargetFormulaLine                   |                       |                        |
| variables Formula Line    | VariablesFormulaLine                |                       |                        |
| variables Formula Line Resizier | VariablesFormulaLineResizier  |                       |                        |
| constraints Formula Line  | ConstraintsFormulaLine              |                       |                        |
| dimensions Container      |                                     | data-name             | yes                    |
| header Folders Item       | Header__HeaderFoldersItem           |                       | yes                    |
| Input Confirm Delete Model Name | HeconfirmedText               |                       |                        |
| input New Model Name      | newModelName                        |                       |                        |
| input New Folder Name     | newFolderName                       |                       |                        |

[Инструкция поиска селекторов](../slectors/instructionSelector.md)

[Инструкция по добавлению нового селектора]()

[Оглавление](../README.md)