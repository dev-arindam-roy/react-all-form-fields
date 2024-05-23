# React Application with all types of form fields

## Check It!

[https://dev-arindam-roy.github.io/react-all-form-fields/](https://dev-arindam-roy.github.io/react-all-form-fields/)

```js
import React, { useState } from "react";
import "./App.css";

const roles = [
  { id: 100, name: "Developer" },
  { id: 101, name: "Manager" },
  { id: 102, name: "DevOops" },
  { id: 103, name: "HR-Team" },
  { id: 104, name: "Account Dept" },
  { id: 105, name: "Business Process Unit" },
];
const sexList = [
  { id: 1, name: "Male" },
  { id: 2, name: "Female" },
  { id: 3, name: "Other" },
];
const skillList = [
  { id: 10, name: "Node Js" },
  { id: 11, name: "React Js" },
  { id: 12, name: "Vue Js" },
  { id: 14, name: "Angular Js" },
  { id: 15, name: "Laravel" },
];
const userObj = {
  name: "",
  email: "",
  mobile: "",
  role: "",
  sex: sexList[0],
  skills: [],
  intro: "",
  educations: [{ name: "", year: "" }],
  frinends: [{ name: "", phone: "" }],
  languages: [""],
};

const App = () => {
  const [user, setUser] = useState(userObj);
  const [userList, setUserList] = useState([]);

  const addMoreLanguageHandler = () => {
    setUser({
      ...user,
      languages: [...user.languages, ""],
    });
  };
  const removeLanguageHandler = (index) => {
    let _tempLanguages = [...user.languages];
    _tempLanguages.splice(index, 1);
    setUser({ ...user, languages: _tempLanguages });
  };
  const addMoreLanguageSetHandler = (evt, index) => {
    let _userLanguages = [...user.languages];
    _userLanguages[index] = evt.target.value;
    setUser({ ...user, languages: _userLanguages });
  };

  const addMoreEducationHandler = () => {
    setUser({
      ...user,
      educations: [...user.educations, { name: "", year: "" }],
    });
  };
  const removeEducationHandler = (index) => {
    let _tempEducations = [...user.educations];
    _tempEducations.splice(index, 1);
    setUser({ ...user, educations: _tempEducations });
  };
  const addMoreEducationNameSetHandler = (evt, index) => {
    let _userEducations = [...user.educations];
    _userEducations[index].name = evt.target.value;
    setUser({ ...user, educations: _userEducations });
  };
  const addMoreEducationYearSetHandler = (evt, index) => {
    let _userEducations = [...user.educations];
    _userEducations[index].year = evt.target.value;
    setUser({ ...user, educations: _userEducations });
  };

  const addMoreFriendsHandler = () => {
    setUser({
      ...user,
      frinends: [...user.frinends, { name: "", phone: "" }],
    });
  };
  const removeFriendHandler = (index) => {
    let _tempFriends = [...user.frinends];
    _tempFriends.splice(index, 1);
    setUser({ ...user, frinends: _tempFriends });
  };
  const addMoreFriendNameSetHandler = (evt, index) => {
    let _userFriends = [...user.frinends];
    _userFriends[index].name = evt.target.value;
    setUser({ ...user, frinends: _userFriends });
  };
  const addMoreFriendPhoneSetHandler = (evt, index) => {
    let _userFriends = [...user.frinends];
    _userFriends[index].phone = evt.target.value;
    setUser({ ...user, frinends: _userFriends });
  };

  const setSexHandler = (evt) => {
    let _sex = sexList.filter(
      (sexObj) => sexObj.id === parseInt(evt.target.value)
    );
    setUser({ ...user, sex: _sex[0] });
  };
  const setSkillHandler = (evt, itemObj) => {
    if (evt.target.checked) {
      setUser({
        ...user,
        skills: [...user.skills, itemObj],
      });
    } else {
      setUser({
        ...user,
        skills: user.skills.filter(
          (obj) => obj.id !== parseInt(evt.target.value)
        ),
      });
    }
    //console.log(user);
  };

  const formSubmitHandler = (e) => {
    e.preventDefault();
    setUserList([...userList, user]);
    formReset();
  };

  const formResetHandler = () => {
    formReset();
  }

  const formReset = () => {
    let _userObj = {
      name: "",
      email: "",
      mobile: "",
      role: "",
      sex: sexList[0],
      skills: [],
      intro: "",
      educations: [{ name: "", year: "" }],
      frinends: [{ name: "", phone: "" }],
      languages: [""],
    };
    setUser(_userObj);
  }

  return (
    <>
      <div className="container">
        <div className="row mt-3 mb-5">
          <div className="col-md-4" style={{backgroundColor: '#e5e5e5', borderRadius: '5px', border: '1px solid #ddd'}}>
            <form onSubmit={formSubmitHandler}>
              <div className="form-group col-md-8">
                <label htmlFor="name">
                  Name: <em>*</em>
                </label>
                <input
                  type="text"
                  name="name"
                  id="name"
                  className="form-control"
                  required
                  placeholder="Name"
                  value={user.name}
                  onChange={(e) => setUser({ ...user, name: e.target.value })}
                />
              </div>
              <div className="form-group col-md-8">
                <label htmlFor="email">
                  Email: <em>*</em>
                </label>
                <input
                  type="email"
                  name="email"
                  id="email"
                  className="form-control"
                  required
                  placeholder="Email"
                  value={user.email}
                  onChange={(e) => setUser({ ...user, email: e.target.value })}
                />
              </div>
              <div className="form-group col-md-8">
                <label htmlFor="mobile">
                  Mobile No: <em>*</em>
                </label>
                <input
                  type="tel"
                  name="mobile"
                  id="mobile"
                  className="form-control"
                  required
                  placeholder="Mobile No"
                  value={user.mobile}
                  onChange={(e) => setUser({ ...user, mobile: e.target.value })}
                />
              </div>
              <div className="form-group col-md-8">
                <label htmlFor="role">
                  Role: <em>*</em>
                </label>
                <select
                  name="role"
                  id="role"
                  className="form-select"
                  required
                  value={user.role}
                  onChange={(e) => setUser({ ...user, role: e.target.value })}
                >
                  <option value="">-Select Role-</option>
                  {roles.length > 0 &&
                    roles.map((item, index) => {
                      return (
                        <option key={"role" + index} value={item.id}>
                          {item.name}
                        </option>
                      );
                    })}
                </select>
              </div>
              <div className="form-group col-md-8">
                <label>
                  Sex: <em>*</em>
                </label>
                <div className="mt-1" style={{ marginLeft: "15px" }}>
                  {sexList.length > 0 &&
                    sexList.map((item, index) => {
                      return (
                        <div
                          className="form-check form-check-inline"
                          key={"sexContainer" + index}
                        >
                          <input
                            type="radio"
                            name="sex"
                            id={"sexOption" + index}
                            className="form-check-input"
                            required
                            value={item.id}
                            checked={user.sex.id === item.id ? true : false}
                            onChange={(e) => setSexHandler(e)}
                          />
                          <label
                            className="form-check-label"
                            htmlFor={"sexOption" + index}
                          >
                            {item.name}
                          </label>
                        </div>
                      );
                    })}
                </div>
              </div>
              <div className="form-group col-md-8">
                <label>
                  Skill (s): <em>*</em>
                </label>
                <div className="mt-1" style={{ marginLeft: "15px" }}>
                  {skillList.length > 0 &&
                    skillList.map((item, index) => {
                      return (
                        <div
                          className="form-check"
                          key={"skillContainer" + index}
                        >
                          <input
                            type="checkbox"
                            name={"skill[" + index + "]"}
                            id={"skillOption" + index}
                            className="form-check-input"
                            minLength="2"
                            value={item.id}
                            checked={user.skills.some(
                              (obj) => obj.id === item.id
                            )}
                            onChange={(e) => setSkillHandler(e, item)}
                          />
                          <label
                            className="form-check-label"
                            htmlFor={"skillOption" + index}
                          >
                            {item.name}
                          </label>
                        </div>
                      );
                    })}
                </div>
              </div>
              <div className="form-group">
                <label>
                  Language (s): <em>*</em>
                </label>
              </div>
              {user.languages.length > 0 &&
                user.languages.map((item, index) => {
                  return (
                    <div className="row" key={"languageContainer" + index}>
                      <div className="form-group col-md-8">
                        <input
                          type="text"
                          name={"languages[" + index + "]"}
                          id={"language-" + index}
                          className="form-control"
                          required
                          placeholder="Language"
                          value={item}
                          onChange={(e) => addMoreLanguageSetHandler(e, index)}
                        />
                      </div>
                      <div className="form-group col-md-4">
                        {index > 0 && (
                          <button
                            type="button"
                            className="btn btn-sm btn-danger"
                            onClick={() => removeLanguageHandler(index)}
                          >
                            [-]
                          </button>
                        )}
                      </div>
                    </div>
                  );
                })}
              <div className="form-group">
                <button
                  type="button"
                  className="btn btn-sm btn-primary"
                  onClick={addMoreLanguageHandler}
                >
                  [+]
                </button>
              </div>
              <div className="form-group">
                <label htmlFor="intro">
                  Self Intro: <em>*</em>
                </label>
                <textarea
                  name="intro"
                  id="intro"
                  className="form-control"
                  maxLength="120"
                  required
                  placeholder="About Yourself"
                  value={user.intro}
                  onChange={(e) => setUser({ ...user, intro: e.target.value })}
                ></textarea>
              </div>
              <div className="form-group">
                <label>
                  Education (s): <em>*</em>
                </label>
              </div>
              {user.educations.length > 0 &&
                user.educations.map((item, index) => {
                  return (
                    <div className="row" key={"educationContainer" + index}>
                      <div className="form-group col-md-8">
                        <input
                          type="text"
                          name={"education[" + index + "]"}
                          id={"education-" + index}
                          className="form-control"
                          required
                          placeholder="Education"
                          value={item.name}
                          onChange={(e) =>
                            addMoreEducationNameSetHandler(e, index)
                          }
                        />
                        {index > 0 && (
                          <button
                            type="button"
                            className="btn btn-sm btn-danger mt-1"
                            onClick={() => removeEducationHandler(index)}
                          >
                            [-]
                          </button>
                        )}
                      </div>
                      <div className="form-group col-md-4">
                        <input
                          type="text"
                          name={"year[" + index + "]"}
                          id={"year-" + index}
                          className="form-control"
                          required
                          placeholder="Year"
                          value={item.year}
                          onChange={(e) =>
                            addMoreEducationYearSetHandler(e, index)
                          }
                        />
                      </div>
                    </div>
                  );
                })}
              <div className="form-group" style={{ textAlign: "right" }}>
                <button
                  type="button"
                  className="btn btn-sm btn-primary"
                  onClick={addMoreEducationHandler}
                >
                  [+]
                </button>
              </div>
              <div className="form-group">
                <label>
                  Friend (s): <em>*</em>
                </label>
              </div>
              {user.frinends.length > 0 &&
                user.frinends.map((item, index) => {
                  return (
                    <div className="row" key={"friendContainer" + index}>
                      <div className="col-md-8">
                        <div className="form-group">
                          <input
                            type="text"
                            name={"friend_name[" + index + "]"}
                            id={"friendName-" + index}
                            className="form-control"
                            required
                            placeholder="Name"
                            value={item.name}
                            onChange={(e) =>
                              addMoreFriendNameSetHandler(e, index)
                            }
                          />
                        </div>
                        <div className="form-group">
                          <input
                            type="tel"
                            name={"friend_phone[" + index + "]"}
                            id={"friendPhone-" + index}
                            className="form-control"
                            required
                            placeholder="Phone"
                            value={item.phone}
                            onChange={(e) =>
                              addMoreFriendPhoneSetHandler(e, index)
                            }
                          />
                        </div>
                      </div>
                      <div className="col-md-4" style={{ textAlign: "right" }}>
                        {index > 0 && (
                          <button
                            type="button"
                            className="btn btn-sm btn-danger"
                            style={{ marginTop: "2px" }}
                            onClick={() => removeFriendHandler(index)}
                          >
                            [-]
                          </button>
                        )}
                      </div>
                    </div>
                  );
                })}
              <div className="form-group">
                <button
                  type="button"
                  className="btn btn-sm btn-primary"
                  onClick={addMoreFriendsHandler}
                >
                  [+]
                </button>
              </div>
              <div className="form-group mt-3">
                <button type="submit" className="btn btn-success">
                  SAVE
                </button>
                <button type="button" className="btn btn-danger mx-2" onClick={formResetHandler}>
                  RESET
                </button>
              </div>
            </form>
            <div className="mt-3" style={{wordWrap: 'break-word'}}>{JSON.stringify(user)}</div>
          </div>
          <div className="col-md-8">
            <div style={{ textAlign: "right", fontWeight: 600 }}>
              Total Users: {userList.length}
            </div>
            <table className="table table-bordered table-striped table-hover table-sm">
              <thead>
                <tr>
                  <th>SL</th>
                  <th>NAME</th>
                  <th>EMAIL</th>
                  <th>MOBILE</th>
                  <th>SEX</th>
                  <th>ROLE</th>
                  <th>SKILLS</th>
                  <th>EDUCATION</th>
                  <th>FRIENDS</th>
                </tr>
              </thead>
              <tbody>
                {userList.length > 0 &&
                  userList.map((userObj, index) => {
                    return (
                      <tr key={"userTr" + index}>
                        <td>{index + 1}</td>
                        <td>{userObj.name}</td>
                        <td>{userObj.email}</td>
                        <td>{userObj.mobile}</td>
                        <td>{userObj.sex.name}</td>
                        <td>
                          {roles.length > 0 &&
                            roles.map((v, i) => {
                              return (
                                v.id === parseInt(userObj.role) && (
                                  <span key={i}>{v.name}</span>
                                )
                              );
                            })}
                        </td>
                        <td>
                          {userObj.skills.length > 0 &&
                            userObj.skills.map((skill, skillIndex) => {
                              return (
                                <li key={"skill" + index + skillIndex}>
                                  {skill.name}
                                </li>
                              );
                            })}
                        </td>
                        <td>
                          {userObj.educations.length > 0 &&
                            userObj.educations.map(
                              (education, educationIndex) => {
                                return (
                                  <li
                                    key={"education" + index + educationIndex}
                                  >
                                    {education.name}{" "}
                                    <small>
                                      <i>({education.year})</i>
                                    </small>
                                  </li>
                                );
                              }
                            )}
                        </td>
                        <td>
                          {userObj.frinends.length > 0 &&
                            userObj.frinends.map((frinend, frinendIndex) => {
                              return (
                                <li key={"frinend" + index + frinendIndex}>
                                  {frinend.name}
                                  <br />
                                  <small>
                                    <i>({frinend.phone})</i>
                                  </small>
                                </li>
                              );
                            })}
                        </td>
                      </tr>
                    );
                  })}
              </tbody>
            </table>
          </div>
        </div>
      </div>
    </>
  );
};

export default App;

```

# Another One

```js
import React, { useState } from 'react';

const citiesArrObj = [
  { id: 1, name: 'Kolkata' },
  { id: 2, name: 'Mumbai' },
  { id: 3, name: 'Delhi' },
  { id: 4, name: 'Channei' },
  { id: 5, name: 'Rajasthan' },
  { id: 6, name: 'Madurai' },
  { id: 7, name: 'Panjab' },
  { id: 8, name: 'Bangalore' },
  { id: 9, name: 'Karala' },
  { id: 10, name: 'Kashmir' },
];

const sexArr = ['Male', 'Female', 'Others'];

const expLevelsArrObj = [
  { id: 1, name: 'Expert', level: 5 },
  { id: 2, name: 'Senior', level: 4 },
  { id: 3, name: 'Medium', level: 3 },
  { id: 4, name: 'Intermidiate', level: 2 },
  { id: 5, name: 'Bigener', level: 1 },
];

const skillsArrObj = [
  { id: 1, name: 'Laravel', type: 'Backend' },
  { id: 2, name: 'Node Js', type: 'Backend' },
  { id: 3, name: 'Python', type: 'Backend' },
  { id: 4, name: 'React Js', type: 'Frontend' },
  { id: 5, name: 'Angular Js', type: 'Frontend' },
  { id: 6, name: 'Vue Js', type: 'Frontend' },
  { id: 7, name: 'MySQL', type: 'Database' },
  { id: 8, name: 'MongoDB', type: 'Database' },
  { id: 9, name: 'Sqlite', type: 'Database' },
  { id: 10, name: 'Bootstrap', type: 'UI/UX' },
];

const defaultUserState = {
  firstname: '',
  lastname: '',
  email: '',
  phonenumber: '',
  address: '',
  city: '',
  sex: sexArr[0],
  exp: [],
  skills: [],
};

const UseStateBsApplication = () => {
  const [user, setUser] = useState(defaultUserState);
  const [userArrObj, setUserArrObj] = useState([]);
  const handleFormSubmit = (e) => {
    e.preventDefault();
    setUserArrObj([...userArrObj, user]);
    handleFormReset();
  };
  const handleFormReset = () => {
    setUser(defaultUserState);
  }
  return (
    <>
      <div className='container py-5'>
        <div className='row'>
          <div className='col-md-4'>
            <div className='card'>
              <div className='card-header'>
                <h3>User Form</h3>
              </div>
              <div className='card-body'>
                <form onSubmit={handleFormSubmit}>
                  <div className='form-group mb-2'>
                    <label htmlFor='firstname'>First Name:</label>
                    <input
                      type='text'
                      name='firstname'
                      id='firstname'
                      className='form-control'
                      placeholder='First Name'
                      value={user.firstname}
                      onChange={(e) =>
                        setUser({ ...user, firstname: e.target.value })
                      }
                    />
                  </div>
                  <div className='form-group mb-2'>
                    <label htmlFor='lastname'>Last Name:</label>
                    <input
                      type='text'
                      name='lastname'
                      id='lastname'
                      className='form-control'
                      placeholder='Last Name'
                      value={user.lastname}
                      onChange={(e) =>
                        setUser({ ...user, lastname: e.target.value })
                      }
                    />
                  </div>
                  <div className='form-group mb-2'>
                    <label htmlFor='email'>Email Id:</label>
                    <input
                      type='email'
                      name='email'
                      id='email'
                      className='form-control'
                      placeholder='Email Id'
                      value={user.email}
                      onChange={(e) =>
                        setUser({ ...user, email: e.target.value })
                      }
                    />
                  </div>
                  <div className='form-group mb-2'>
                    <label htmlFor='phonenumber'>Phone Number:</label>
                    <input
                      type='tel'
                      name='phonenumber'
                      id='phonenumber'
                      className='form-control'
                      placeholder='Phone Number'
                      value={user.phonenumber}
                      onChange={(e) =>
                        setUser({ ...user, phonenumber: e.target.value })
                      }
                    />
                  </div>
                  <div className='form-group mb-2'>
                    <label htmlFor='address'>Address:</label>
                    <textarea
                      name='address'
                      id='address'
                      className='form-control'
                      value={user.address}
                      onChange={(e) =>
                        setUser({ ...user, address: e.target.value })
                      }
                    ></textarea>
                  </div>
                  <div className='form-group mb-2'>
                    <label htmlFor='city'>City:</label>
                    <select
                      name='city'
                      id='city'
                      className='form-select'
                      value={user.city}
                      onChange={(e) =>
                        setUser({ ...user, city: e.target.value })
                      }
                    >
                      <option value=''>-City-</option>
                      {citiesArrObj.length > 0 &&
                        citiesArrObj.map((item, index) => {
                          return (
                            <option key={index} value={item.id}>
                              {item.name}
                            </option>
                          );
                        })}
                    </select>
                  </div>
                  <div className='form-group mb-2'>
                    <label>Sex:</label>
                    {sexArr.length > 0 &&
                      sexArr.map((item, index) => {
                        return (
                          <div className='form-check ms-4' key={index}>
                            <input
                              type='radio'
                              name='sex'
                              className='form-check-input'
                              id={'sex' + index}
                              checked={
                                user.sex === '' && index === 0
                                  ? true
                                  : user.sex === item
                                  ? true
                                  : false
                              }
                              value={item}
                              onChange={(e) =>
                                setUser({ ...user, sex: e.target.value })
                              }
                            />
                            <label
                              htmlFor={'sex' + index}
                              className='form-check-label'
                            >
                              {item}
                            </label>
                          </div>
                        );
                      })}
                  </div>
                  <div className='form-group mb-2'>
                    <label>Exp Level:</label>
                    {expLevelsArrObj.length > 0 &&
                      expLevelsArrObj.map((item, index) => {
                        return (
                          <div className='form-check ms-4' key={index}>
                            <input
                              type='checkbox'
                              name='exp'
                              className='form-check-input'
                              id={'exp' + index}
                              value={item.id}
                              checked={user.exp.includes(item.id.toString())}
                              onChange={(e) =>
                                e.target.checked
                                  ? setUser({
                                      ...user,
                                      exp: [...user.exp, e.target.value],
                                    })
                                  : setUser({
                                      ...user,
                                      exp: user.exp.filter(
                                        (v) => v !== e.target.value
                                      ),
                                    })
                              }
                            />
                            <label
                              htmlFor={'exp' + index}
                              className='form-check-label'
                            >
                              {item.name}
                              <span className='ms-2'>
                                <small>({item.level})</small>
                              </span>
                            </label>
                          </div>
                        );
                      })}
                  </div>
                  <div className='form-group mb-2'>
                    <label>Skills:</label>
                    {skillsArrObj.length > 0 &&
                      skillsArrObj.map((item, index) => {
                        return (
                          <div className='form-check ms-4' key={index}>
                            <input
                              type='checkbox'
                              name='skills'
                              className='form-check-input'
                              id={'skill' + index}
                              value={item.id}
                              checked={user.skills.includes(item.id.toString())}
                              onChange={(e) =>
                                e.target.checked
                                  ? setUser({
                                      ...user,
                                      skills: [...user.skills, e.target.value],
                                    })
                                  : setUser({
                                      ...user,
                                      skills: user.skills.filter(
                                        (v) => v !== e.target.value
                                      ),
                                    })
                              }
                            />
                            <label
                              htmlFor={'skill' + index}
                              className='form-check-label'
                            >
                              {item.name}
                              <span className='ms-2'>
                                <small>[{item.type}]</small>
                              </span>
                            </label>
                          </div>
                        );
                      })}
                  </div>
                  <div className='form-group mb-2 mt-4 text-end'>
                    <button type='button' className='btn btn-danger' onClick={handleFormReset}>
                      Reset
                    </button>
                    &nbsp;
                    <button type='submit' className='btn btn-success'>
                      Submit
                    </button>
                  </div>
                </form>
              </div>
            </div>
          </div>
          <div className='col-md-8'>
            <div className='row'>
              <div className='col-md-12'>
                <div className='alert alert-success'>
                  <textarea className='form-control' value={JSON.stringify(user)} readOnly></textarea>
                </div>
              </div>
              <div className='col-md-12'>
                <div className='alert alert-primary'>
                  <textarea className='form-control' value={JSON.stringify(userArrObj)} readOnly></textarea>
                </div>
              </div>
              <div className='col-md-12'>
                <table className='table table-bordered table-sm'>
                    <thead>
                        <tr>
                            <th>SL</th>
                            <th>Name</th>
                            <th>Contact</th>
                            <th>Address</th>
                            <th>Skill</th>
                            <th>Exp Level</th>
                            <th>#</th>
                        </tr>
                    </thead>
                    <tbody>
                        {
                            userArrObj.length > 0 &&
                            userArrObj.map((item, index) => {
                                return (
                                    <tr key={index}>
                                        <td>{index + 1}</td>
                                        <td>
                                            {item.firstname} {item.lastname} <br/> {item.sex}
                                        </td>
                                        <td>
                                            {item.email} <br/> {item.phonenumber}
                                        </td>
                                        <td>
                                            {
                                                citiesArrObj.length > 0 &&
                                                citiesArrObj.map((v, i) => {
                                                    return v.id === parseInt(item.city) && (<span key={i}>{v.name}</span>)
                                                })
                                            }
                                            <br/>
                                            {item.address}
                                        </td>
                                        <td>
                                            <ul>
                                                {
                                                    skillsArrObj.length > 0 &&
                                                    skillsArrObj.map((v, i) => {
                                                        return item.skills.includes(v.id.toString()) && (<li key={i}>{v.name} ({v.type})</li>)
                                                    })
                                                }
                                            </ul>
                                        </td>
                                        <td>
                                            <ul>
                                                {
                                                    expLevelsArrObj.length > 0 &&
                                                    expLevelsArrObj.map((v, i) => {
                                                        return item.exp.includes(v.id.toString()) && (<li key={i}>{v.name} ({v.level})</li>)
                                                    })
                                                }
                                            </ul>
                                        </td>
                                        <td>#</td>
                                    </tr>
                                )
                            })
                        }
                    </tbody>
                </table>
              </div>
            </div>
          </div>
        </div>
      </div>
    </>
  );
};

export default UseStateBsApplication;
```