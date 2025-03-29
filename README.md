import { useState } from "react"; import { Card, CardContent } from "@/components/ui/card"; import { Button } from "@/components/ui/button"; import { Input } from "@/components/ui/input"; import { Tabs, TabsList, TabsTrigger, TabsContent } from "@/components/ui/tabs";

export default function PhysioSriLankaApp() { const [role, setRole] = useState("admin"); const [password, setPassword] = useState(""); const [isAuthenticated, setIsAuthenticated] = useState(false);

const handleLogin = () => { // Mock authentication logic if (password === "password") { setIsAuthenticated(true); } };

return ( <div className="flex flex-col items-center p-6"> <h1 className="text-2xl font-bold mb-4">Physio Sri Lanka App</h1> {!isAuthenticated ? ( <Card className="p-4 w-96"> <Tabs defaultValue="admin" className="w-full"> <TabsList className="flex justify-center mb-4"> <TabsTrigger value="admin" onClick={() => setRole("admin")}>Admin</TabsTrigger> <TabsTrigger value="therapist" onClick={() => setRole("therapist")}>Therapist</TabsTrigger> <TabsTrigger value="patient" onClick={() => setRole("patient")}>Patient</TabsTrigger> </TabsList> <TabsContent value={role}> <Input type="password" placeholder="Enter password" value={password} onChange={(e) => setPassword(e.target.value)} className="mb-4" /> <Button onClick={handleLogin}>Login</Button> </TabsContent> </Tabs> </Card> ) : ( <Card className="p-6 w-full max-w-md"> <h2 className="text-xl font-semibold mb-4">Welcome, {role}</h2> {role === "admin" && <p>Manage patients, allocate therapists, and view all records.</p>} {role === "therapist" && <p>View assigned patients, log visits, and update profiles.</p>} {role === "patient" && <p>View your medical records (read-only).</p>} <Button className="mt-4" onClick={() => setIsAuthenticated(false)}>Logout</Button> </Card> )} </div> ); }

