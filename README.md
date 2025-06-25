- 👋 Hi, I’m @abhijay998
- 👀 I’m interested in proggraming/coding

I made a Library for JS called Webx.js it Helps you to make better web apps fast and make them dynamic It has two syntax types ["tree", "base"] tree is scalable and structured code where as basic is simple and it can be used for fast protyping want to make a todo app 

```JS
AddMaterial3Lib();
const Styles = {
    TodoCont: `backdrop-blur-lg bg-white/10 text-black p-6 m-4 flex justify-between rounded-lg`,
    root: `${
        SetMdTheme({
            primaryC: Colors.cyan[500],
            OnPrimaryC: colors.white,
        })
    }`
}

const inp = input(getById('Body'), 'text', 'todo', 'class', `
    backdrop-blur-lg bg-white/10 w-full p-4 rounded-lg text-black m-2 outline-none focus:ring-cyan-500 focus:ring-2
`);
const MyApp = webx.CreateApp({
    home: Home({
        style: Styles.root,
        scaf: Scaf({
            body: Body({
                Content: [
                    webx.createElement({
                        tag: 'div',
                        attribute: {
                            key: 'class',
                            value: 'p-4'
                        }, html: [
                            h1('Todo', null, 'class', 'text-4xl m-2 text-black'),
                            inp,
                            webx.createElement({
                                tag: 'md-filled-button',
                                html: h1('Add'),
                                attribute: {
                                    key: 'class',
                                    value: 'm-2'
                                }, event: 'click',
                                eventCode: function () {
                                    const ids = `TODO-${Time({
                                        hour: false,
                                        min: false,
                                        sec: true,
                                    })}`;

                                    webx.Storage.Local.Add({ 
                                        key: ids, 
                                        value: inp.value,
                                    }) 

                                    webx.createElement({
                                        tag: 'div',
                                        parent: getById('todos'), 
                                        attribute: [
                                            { 
                                                key: 'class', 
                                                value: Styles.TodoCont 
                                            }, {
                                                key: 'id',
                                                value: ids,
                                            } 
                                        ], html: [
                                            webx.createElement({
                                                tag: 'span',
                                                html: inp.value,
                                            }),

                                            webx.createElement({
                                                tag: 'span',
                                                html: webx.createElement({
                                                    tag: 'md-filled-button',
                                                    html: h1('Remove'),
                                                    event: 'click',
                                                    eventCode: function () {
                                                        const TodoCont = getById('todos');
                                                        const toItem = getById(ids)
                                                        if (toItem) TodoCont.removeChild(toItem);
                                                        else { log('err', Colors.red[500]) }
                                                        webx.Storage.Local.Remove(ids);
                                                    } 
                                                }), 
                                            })
                                        ]
                                    });
                                }
                            }),
                        ],
                    }),

                    webx.createElement({
                        tag: 'div',
                        html: '',
                        attribute: {
                            key: 'id', 
                            value: 'todos'
                        }
                    })
                ],
            }),
        }),
    }),
});


Object.keys(localStorage).forEach(key => {
    if (key.startsWith('TODO-')) {
        const value = webx.Storage.Local.GetItem(key);

        webx.createElement({
            tag: 'div',
            parent: getById('todos'),
            attribute: [
                { key: 'class', value: Styles.TodoCont },
                { key: 'id', value: key }
            ],
            html: [
                webx.createElement({
                    tag: 'span',
                    html: value,
                }),
                webx.createElement({
                    tag: 'span',
                    html: webx.createElement({
                        tag: 'md-filled-button',
                        html: h1('Remove'),
                        event: 'click',
                        eventCode: function () {
                            const TodoCont = getById('todos');
                            const toItem = getById(key);
                            if (toItem) {
                                TodoCont.removeChild(toItem);
                                webx.Storage.Local.Remove(key);
                            }
                        }
                    }),
                })
            ]
        });
    }
});

webx.keyEvent({
    keyDown: true,
    key: 'Enter',
    eventCode: function () {
        const ids = `TODO-${Time({
            hour: false,
            min: false,
            sec: true,
        })}`;

        webx.Storage.Local.Add({ 
            key: ids, 
            value: inp.value,
        }) 

        webx.createElement({
            tag: 'div',
            parent: getById('todos'), 
            attribute: [
                { 
                    key: 'class', 
                    value: Styles.TodoCont 
                }, {
                    key: 'id',
                    value: ids,
                } 
            ], html: [
                webx.createElement({
                    tag: 'span',
                    html: inp.value,
                }),

                webx.createElement({
                    tag: 'span',
                    html: webx.createElement({
                        tag: 'md-filled-button',
                        html: h1('Remove'),
                        event: 'click',
                        eventCode: function () {
                            const TodoCont = getById('todos');
                            const toItem = getById(ids)
                            if (toItem) TodoCont.removeChild(toItem);
                            else { log('err', Colors.red[500]) }
                            webx.Storage.Local.Remove(ids);
                        } 
                    }), 
                })
            ]
        });
    }
});
```

that is all what you need for tree structure to be precise (189 lines of code including storage and data privacy as the data is stored locally on the users machine)![iphone](https://github.com/user-attachments/assets/a752eef6-a735-4104-bbc9-928b0bbc7de8)

but we can make the code shorter by base syntax moving the code all the way to less than 100 lines of code I hope you will like it check it out on it is completly free the only way by which you can contribute me is by staring a repo https://github.com/abhijay998/webx.js- 

although my styling is not that great hear but the core structure and logic works 
